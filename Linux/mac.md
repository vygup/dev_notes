linux
    sudo ifconfig eth0 down

    sudo ifconfig eth0 hw ether XX:XX:XX:XX:XX:XX

    sudo ifconfig eth0 up

Mac
    #Обычно может без этой команды не работать
    sudo /System/Library/PrivateFrameworks/Apple80211.framework/Versions/Current/Resources/airport -z

    sudo ifconfig en0 ether XX:XX:XX:XX:XX:XX