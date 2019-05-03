9 december 2018



                                          Apache Lounge Distribution

     mod_security-2.9.3 build with libxml2-2.9.8 lua-5.1.5 pcre-8.42 yajl-2.1.0 curl-7.62.0 for 2.4 Win64 VC15

# Original source by: Ivan Ristic <ivanr@webkreator.com>
# Original Home: http://www.modsecurity.org/
# Binary by: Steffen
# Mail: info@apachelounge.com
# Home: http://www.apachelounge.com/


# Install:

- Copy mod_security2.so to your apache/modules folder

- Copy yajl.dll to your apache/bin folder


# Add to your httpd.conf:

  LoadModule security2_module modules/mod_security2.so

- Enable the module unique_id by uncommenting:

  LoadModule unique_id_module modules/mod_unique_id.so


# Configuration: see the included documentation

# Rules and documentation : http://www.modsecurity.org/


# A very quick start:

SecRuleEngine On
SecDefaultAction "deny,phase:2,status:403"

## -- rule --


SecRule ARGS "\.\./" "t:normalizePathWin,id:50904,severity:4,t:none,t:urlDecodeUni,t:htmlEntityDecode,t:lowercase,msg:'Drive Access'" 


Call your site with: 

http://www.xxxx.com/?abc=../../ 

You should get a access denied and is logged in the Apache error.log, it is triggered by the above rule

Enjoy,

Steffen