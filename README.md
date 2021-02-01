# php-serialization-README.md

Source: https://www.youtube.com/watch?v=HaW15aMzBUM&t=1257s

#### Create a PHP file called code.php and run with the command 'php code.php'

    <?php

    class User
    {
            public $username;
            public $isAdmin;

            public function PrintData(){
                    if ($this->isAdmin){
                            echo $this->username . " is an admin\n";
                    } else {
                            echo $this->username . " is not an admin\n";
                    }
            }
    }

    $obj = new User();              # instantiate the class
    $obj->username = 'chris';       # set username
    $obj->isAdmin = False;          # set isAdmin
    $obj->PrintData();              # call the PrintData() function that echoes whether username is an admin or not
    
    echo serialize($obj);           # show the serialized object
    
    ?>


#### Make the script callable from an HTTP server with $_GET['arepo'] and host on apache2 or php -S 127.0.0.1:80. Call it with 'curl -XGET -d 'O:4:%22User%22:2:{s:8:%22username%22;s:5:%22chris%22;s:7:%22isAdmin%22;b:1;}' localhost/code.php' or http://127.0.0.1/code.php?arepo=O:4:%22User%22:2:{s:8:%22username%22;s:5:%22chris%22;s:7:%22isAdmin%22;b:1;}

    <?php

    class User
    {
            public $username;
            public $isAdmin;

            public function PrintData(){
                    if ($this->isAdmin){
                            echo $this->username . " is an admin\n";
                    } else {
                            echo $this->username . " is not an admin\n";
                    }
            }
    }

    $obj = new User();
    $obj->username = 'chris';
    $obj->isAdmin = False;

    //$obj = unserialize($_GET['arepo']);
    $obj->PrintData();
    echo serialize($obj);


    ?>



