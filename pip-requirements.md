# How to install Python packages with pip and requirements.txt

If you are managing Python packages (libraries) with pip, you can use the configuration file requirements.txt to install the specified packages with the specified version at once.

User Guide — pip 9.0.1 documentation - https://pip.pypa.io/en/latest/user_guide/#requirements-files
Here, the following contents will be described.

## Install multiple packages with pip: -r requirements.txt
How to write configuration file requirements.txt
Export current environment configuration file: pip freeze

The following command will install the packages according to the configuration file requirements.txt.

>$ pip install -r requirements.txt  

The name of the configuration file is arbitrary but the name requirements.txt is often used.

Put requirements.txt in the directory where the command will be executed. If it is in another directory, specify the path.

## How to write configuration file "requirements.txt"

>###### Requirements without Version Specifiers ######`  
>nose  
>nose-cov  
>beautifulsoup4  
>  
>###### Requirements with Version Specifiers ######`
>docopt == 0.6.1             # Version Matching. Must be version 0.6.1  
>keyring >= 4.1.1            # Minimum version 4.1.1  
>coverage != 3.5             # Version Exclusion. Anything except version 3.5  
>Mopidy-Dirble ~= 1.1        # Compatible release. Same as >= 1.1, == 1.*  

Like Python code, you can write comments using #.

You can specify the version with ==, >, >=, <, <=, etc. If the version is omitted, the latest version is installed.

Two conditions can be specified with AND by separating them with a comma ,.  
In the following example, a version of 1.0 or more and2.0 or less is installed.  
>package >= 1.0, <=2.0


## Export current environment configuration file: pip freeze

pip freeze outputs the package and version installed in the current environment in the form of a configuration file that can be used with pip install -r.

>$ pip freeze
>agate==1.6.0
>agate-dbf==0.2.0
>agate-excel==0.2.1
>agate-sql==0.5.2

If you output pip freeze to a file with redirect >, you can use that file to install packages of the same version as the original environment in another environment.

The following flow:

First, output requirements.txt to a file.  
 >$ pip freeze > requirements.txt
 
 Copy or move this requirements.txt to another environment and install with it.  
 
 >$ pip install -r requirements.txt
 
 
