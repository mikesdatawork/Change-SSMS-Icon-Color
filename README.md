![MIKES DATA WORK GIT REPO](https://raw.githubusercontent.com/mikesdatawork/images/master/git_mikes_data_work_banner_01.png "Mikes Data Work")        

# Change SSMS Icon Color
**Post Date: November 3, 2016**        



## Contents    
- [About Process](##About-Process)  
- [SQL Logic](#SQL-Logic)  
- [Build Info](#Build-Info)  
- [Author](#Author)  
- [License](#License)       

## About-Process

<p>Whenever you're done configuring a new Database Server you might notice the SSMS Server Icon is still representing a white color rather than green. This is because you forgot to enable the remote admin setting on the server firewall. No worries on logging back into the server and setting it directly cause you can do this directly from the SSMS client (provided the SQL Service account has local rights in the OS).</p>

![SQL SSMS Icon Color](https://mikesdatawork.files.wordpress.com/2016/11/image001.png "SQL SSMS Icon Color")



## SQL-Logic
```SQL
use master;
 
set nocount on
 
exec master..sp_configure 'show advanced options', '1';
 
exec master..sp_configure 'xp_cmdshell', '1' reconfigure with override;
 
exec master..xp_cmdshell 'netsh firewall set service RemoteAdmin enable'; --deprecated, but still works.
 
exec master..xp_cmdshell 'netsh advfirewall firewall set rule group="remote administration" new enable=yes';
 
go
```
![SSMS Firewall Icon]( https://mikesdatawork.files.wordpress.com/2016/11/image002.png "SSMS Firewall Icon")
 


[![WorksEveryTime](https://forthebadge.com/images/badges/60-percent-of-the-time-works-every-time.svg)](https://shitday.de/)

## Build-Info

| Build Quality | Build History |
|--|--|
|<table><tr><td>[![Build-Status](https://ci.appveyor.com/api/projects/status/pjxh5g91jpbh7t84?svg?style=flat-square)](#)</td></tr><tr><td>[![Coverage](https://coveralls.io/repos/github/tygerbytes/ResourceFitness/badge.svg?style=flat-square)](#)</td></tr><tr><td>[![Nuget](https://img.shields.io/nuget/v/TW.Resfit.Core.svg?style=flat-square)](#)</td></tr></table>|<table><tr><td>[![Build history](https://buildstats.info/appveyor/chart/tygerbytes/resourcefitness)](#)</td></tr></table>|

## Author

[![Gist](https://img.shields.io/badge/Gist-MikesDataWork-<COLOR>.svg)](https://gist.github.com/mikesdatawork)
[![Twitter](https://img.shields.io/badge/Twitter-MikesDataWork-<COLOR>.svg)](https://twitter.com/mikesdatawork)
[![Wordpress](https://img.shields.io/badge/Wordpress-MikesDataWork-<COLOR>.svg)](https://mikesdatawork.wordpress.com/)

    
## License
[![LicenseCCSA](https://img.shields.io/badge/License-CreativeCommonsSA-<COLOR>.svg)](https://creativecommons.org/share-your-work/licensing-types-examples/)

![Mikes Data Work](https://raw.githubusercontent.com/mikesdatawork/images/master/git_mikes_data_work_banner_02.png "Mikes Data Work")

