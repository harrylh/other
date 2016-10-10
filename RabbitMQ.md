# RabbitMQ Server FAQ [2016/10/10]  
* erlang >= R16B-03 is needed by rabbitmq  
 1.  erlang 19 is not supported, use previous versino  
 2.  download rabbitmq pkg from [here](https://github.com/rabbitmq/erlang-rpm/releases)   
 
* login failed on localhost using "guest"  
 *  chagne firewall: 
    firewall-cmd --zone=public --add-port=15672/tcp --permanent  
    firewall-cmd --reload  
 *  RabbitMQ default user "guest/guest" is Only valid for localhost:15672.  It could not be used to support remote machine login.  
 *  rabbitmqctl add_user admin admin   //add acount   
 *  rabbitmqctl set_user_tags admin administrator   //set role  
 *  rabbitmqctl set_permissions -p "/" admin ".*" ".*" ".*"    //set access control  
 
* RabbitMQ example program Dial() failed with 501 timeout or no access to vhost  
 *  rabbitmqctl set_permissions -p "/" admin ".*" ".*" ".*"    //set access control  
 *  use 5672 default port, 15672 is web ui port. 
