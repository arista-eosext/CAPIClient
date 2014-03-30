CAPIClient
==========
Client library for Command API.

## INSTALLATION
   
### Requirements:                                     
* Python 2.6 or later: http://www.python.org
* jsonrpclib: https://github.com/joshmarshall/jsonrpclib

Simply add CAPIClient.py to the Python path.

Usage example:

```
import CAPIClient

client = CAPIClient.CommandApiClient( <hostname>, <username>, <password> )
res = client.runEnableCmds( [ 'show version', 
                            'show interfaces' ] )
print 'TotalMemory: %d' % res[ 0 ][ 'memTotal' ]
print 'Interfaces: %s' % res[ 1 ][ 'interfaces' ].keys()

et1 = client.interface( 'Ethernet1' )
et1.runConfigCmds( 'description This is Ethernet1')
print et1.status()[ 'description' ]

vlan1 = client.vlan( 1234 )
print vlan1.status()
```

## COMPATIBILITY 
Version 1.0 has been developed and tested using Python 2.7,
but should work on any system supporting Python 2.6 or
later. Please reach out to support@aristanetworks.com for
assistance if needed.

## LIMITATIONS
Command API is only available starting EOS-4.12.0.

In EOS-4.12.0-3, InterfaceClient.runConfigCmds( ...  ) raises
ProtocolError for interface ranges. This bug is fixed in later
releases.

## LICENSE
BSD-3, See LICENSE file