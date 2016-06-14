---
---

# Automating Attribute Release

One of the most complex tasks an Identity Provider (IdP) administrator has to keep up with is the constantly changing set of services and attribute requirements each service has.

**Note:** For Shibboleth IdPv3 installed using the HKAF IdP Installer attribute release is based on information provided in the Federation Metadata. There is no need to configure additional federation filter policies.  

The HKAF Federation Registry service automates this process in 2 ways:

> 1. Keeping metadata up to date in a standards compliant manner to advertise what IdPs offer and what SPs have been approved to receive (This is useful for non Shibboleth, SAML 2 MD specification compliant implementations)

> 2. Generation of Shibboleth 2 compliant Attribute-Filter policies, which are published over https and automatically consumed by IdP. Using this approach your IdP is always in Sync.

## Automating attribute release for Shibboleth 2 IdP

> 1. Determine your unique attribute filter URL via one of the methods below:

If you've received your IdP acceptance email with the subject "Your Identity Provider has been accepted" go to the Configure Attribute Release section to find the URL to use.

If you have an existing IdP, navigate to Federation Registry and view your IdP details. In the SAML section and under the Attribute Filter sub section you will find the required URL. 
This is the value of YOUR UNIQUE URL that is used below.


> 2. Navigate to your IdP configuration directory (generally /opt/shibboleth-idp/conf). Run wget (or similar under windows)

    wget [YOUR UNIQUE URL] -O AAF-attribute-filter.xml

Check that the file downloads correctly and make sure it is writable by the user your IDP tomcat container runs as. You may need to install the default SSL CA bundle on your system if you have SSL verification problems. Please contact your system administrator who will be able to install appropriate packages.

If you view the first few lines of the downloaded file you should see that it indicates it was uniquely created for your IdP and its associated entityID.

> 3. Edit the file service.xml to contain the following (note the use of the XML srv namespace which is required on Shibboleth IdP 2.2 and greater):

    <srv:Service id="shibboleth.AttributeFilterEngine"
              configurationResourcePollingFrequency="PT2H0M0.000S" 
          configurationResourcePollingRetryAttempts="10"
          xsi:type="attribute-afp:ShibbolethAttributeFilteringEngine">
        <srv:ConfigurationResource file="/opt/shibboleth-idp/conf/attribute-filter.xml" xsi:type="resource:FilesystemResource" />
             <srv:ConfigurationResource xsi:type="resource:FileBackedHttpResource"
                   url="[YOUR UNIQUE URL]"
                   file="/opt/shibboleth-idp/conf/HKAF-attribute-filter.xml" />

    </srv:Service>

Here is an example of ours (this is a pre shibboleth 2.2 IdP example, note the lack of XML srv namespace which is required on Shibboleth IdP 2.2 and a difference in the way polling frequency is defined):

    <Service id="shibboleth.AttributeFilterEngine" configurationResourcePollingFrequency="1800000" 
    configurationResourcePollingRetryAttempts="10" xsi:type="attribute-afp:ShibbolethAttributeFilteringEngine">
        <ConfigurationResource  xsi:type="resource:FileBackedHttpResource"
	url="https://ds.test.aaf.edu.au/distribution/attributefilter/299.xml"
	file="/opt/shibboleth-idp/conf/AAF-attribute-filter.xml" />
    </Service> 

> 4. If your IdP is already functioning restart your IdP to pick up these changes. If you are undertaking an initial install continue on with the advertised steps.

## Extra checks you can undertake

The attribute names used in the downloaded policy file HKAF-attribute-filter.xml must match the local attribute names. Check that the attribute names in the downloaded attribute filter against their names in existing configuration files:

attribute-resolver.xml ensure the values for attributeID in the AAF-attribute-filter.xml file map to id values in your resolver eg for auEduPersonSharedToken:

    HKAF-attribute-filter.xml
    <AttributeRule attributeID="auEduPersonSharedToken"><PermitValueRule xsi:type="basic:ANY"/></AttributeRule>

    attribute-resolver.xml
    <resolver:AttributeDefinition id="auEduPersonSharedToken" xsi:type="Simple" xmlns="urn:mace:shibboleth:2.0:resolver:ad"
            sourceAttributeID="auEduPersonSharedToken">

AAF-attribute-filter.xml will likely contain many policies for numerous services. Validating the attributes within the policy for https://manager[.test].aaf.edu.au/shibboleth is more than sufficient.

/opt/shibboleth-idp/uApprove.properties under sections ar.attributes.order and ar.attributes.blacklist ensuring values for attributeID in the AAF-attribute-filter.xml file map to the values configured here.

**Note:** For earlier versions of uApprove these attributes are listed in the file /opt/uApprove/conf/attribute-list (uApprove attribute list) again ensuring values for attributeID in the AAF-attribute-filter.xml file map to the values configured here as your attribute list.