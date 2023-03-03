# Nots about porting a rust app 

Some pure rust applications for porting could still throw errors because they rely on a part of libc API 
which is not implmented yet in relibc. This could result in needed contritbution to relibc library
of redox.
