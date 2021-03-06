${product.name} v${product.version}


This file explains the usages of all the scripts contained within
this directory.

1. README.txt
    - This file

2. kernel-version.txt
    - A simple text file used for storing the version

3. carbon.sh & carbon.bat
    - The main script file used for running the server.

    Usage: carbon.sh [commands] [system-properties]

            commands:
                --debug <port>  Start the server in remote debugging mode.
                                port: The remote debugging port.
                --start		    Start Carbon using nohup
                --stop		    Stop the Carbon server process
                --restart	    Restart the Carbon server process
                --version       The version of the product you are running.

            system-properties:

                -DosgiConsole=[port]
                                Start Carbon with Equinox OSGi console.
                                If the optional 'port' parameter is provided, a
                                telnet port will be opened.

                -DosgiDebugOptions=[options-file]
                                Start Carbon with OSGi debugging enabled.
                                If the optional 'options-file' is provided, the OSGi
                                debug options will be loaded from it.

4. jartobundle.sh script
    - The script file which runs the org.wso2.carbon.jartobundle-tool.jar tool.

    - This tool is capable of converting specified jar files to their corresponding OSGi bundles.

    Usage: jartobundle.sh [source] [destination]

        -- source       source jar file/directory path containing jar file(s) to be converted to
                           OSGi bundle(s)

        -- destination  destination directory path in which the OSGi bundles are to be created

5. ciphertool.sh & ciphertool.bat
    - The script files which run the cipher tool.

    - This tool is mainly used to secure (encrypt) the secrets given in the conf/security/secrets.properties file.
      Apart from that this tool is capable of encrypting and decrypting secrets.

    - Default behaviour of the ciphertool can be changed by modifying the conf/secure-vault.yaml file.

    Usage: ciphertool.sh [<command> <parameter>]

        -- command      -encryptText | -decryptText | -customLibPath

        -- parameter    input to the command

        eg: 1. ciphertool.sh
               Encrypts the secrets in the conf/security/secrets.properties file

            2. ciphertool.sh -encryptText ABC@123
               Encrypts the given parameter "ABC@123"

            3. ciphertool.sh -decryptText XX...XX
               Decrypts the given parameter "XX...XX"

            4. ciphertool.sh -customLibPath /home/user/custom/libs
               Loads the libraries in the given path first and perform the same operation as in eg:1.
               This is an optional flag.

6. dropins.sh & dropins.bat
    - The script files which run the dropins deployer tool.

    - This tool updates the bundles.info file of the specified Carbon Profile.

    Usage : dropins.sh [profile]

        -- profile      name of the Carbon Profile to be updated or keyword 'ALL' to update all the profiles.
