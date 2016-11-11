<!--References present facts that users might need to understand or use a product.-->

## Text-mode installation options

The following options are available for running the installer in text mode.

The syntax for the text-based installation with a specified `pe.conf` file is

~~~
sudo ./puppet-enterprise-installer -c <FULL PATH TO pe.conf>
~~~

When you use the `-c` option, the `pe.conf` file name with full path is required. The command will quit with an error message if you omit it.

When you use the `-c` option, you can also use the following options:

Option          | Definition  |
----------------|:---------------:|
`-D` | The installer will display debugging information | 
`-q` | The installer will run in quiet mode. The installation process will not be displayed. If errors occur during the installation, the command will quit with an error message. | 
`-V` | The installer will display very verbose debugging information. |
`-h` | The installer will display help information.


* * *
