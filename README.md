	 ____                    __
	/\  _`\                 /\ \                     /'\_/`\
	\ \ \/\ \    ___     ___\ \ \/'\      __   _ __ /\      \     __
	 \ \ \ \ \  / __`\  /'___\ \ , <    /'__`\/\`'__\ \ \__\ \  /'__`\
	  \ \ \_\ \/\ \L\ \/\ \__/\ \ \\`\ /\  __/\ \ \/ \ \ \_/\ \/\  __/
	   \ \____/\ \____/\ \____\\ \_\ \_\ \____\\ \_\  \ \_\\ \_\ \____\
	    \/___/  \/___/  \/____/ \/_/\/_/\/____/ \/_/   \/_/ \/_/\/____/

	
	DockerME V0.5 (BETA) FEB 2019
	Docker Hosting Tools
	by Mind.Engineering
	https://mind.engineering/
	Works only on Ubuntu 16.04.4 LTS




## 1. USAGE
Usage: dockerme -argument option1 option2 --subarguments          
           
 
                    Usage: dockerme -argument option1 option2 --subarguments          
           dockerme -i / -u --all                      install dockerme / remove all
           dockerme -yml --list                        list of yml files
           dockerme -c/-o domainename.tld yml          create / override dockers based on docker-compose from yml with specific domaine 
           dockerme -c/-o domainename.tld yml --local  create / override dockers with local entry in /etc/host    
           dockerme -rm domainename.tld                remove dockers, volumes, backup and configuration for specific domainename.tld  
           dockerme -up/down domainename.tld           lunch docker-compose up/down -d for specific domainename.tld  
           dockerme -start/stop domainename.tld        start/stop containers for specific domainename.tld 
           dockerme -log --view / --trancate           read docker log file / trancate docker log file
           dockerme -auditor --dbfs                    Lunch Docker Brech For Security auditing tools 
           dockerme -auditor --lynis                   Lunch Lynis auditing tools
           dockerme -update                            Update dockerme without modifiyng runing containers




## 2. BUILDING .DEB PACKAGE

    sudo apt-get install dh-make devscripts
    cd dockerme-0.1/
    chmod u+x dockerme
    dh_make --indep --createorig
    grep -v makefile debian/rules > debian/rules.new
    mv debian/rules.new debian/rules
    echo dockerme usr/bin > debian/install
    echo "1.0" > debian/source/format
    rm debian/*.ex
    debuild -us -uc
    cd ..
    sudo dpkg -i dockerme_0.1-1_all.deb #for installing program
    sudo dpkg -r dockerme #for removing program
