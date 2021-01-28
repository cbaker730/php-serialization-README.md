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


#### Make the script callable from an HTTP server with $_GET['arepo'] and host on apache2 or php -S 127.0.0.1:80. Call it with 'curl -XGET -d '-serialized object-' localhost/code.php' or http://127.0.0.1/code.php?arepo=-serialized object-

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

    //$obj = new User();
    //$obj->username = 'chris';
    //$obj->isAdmin = False;

    $obj = unserialize($_GET['arepo']);     # the serialized object we pass in needs to instantiate a new User object and set username and isAdmin
    $obj->PrintData();
    
    echo serialize($obj);

    ?>



