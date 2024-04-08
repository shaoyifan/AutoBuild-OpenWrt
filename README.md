 echo "src-git smpackage https://github.com/kenzok8/small-package" >> ./feeds.conf.default



./scripts/feeds update -a
./scripts/feeds install -a


rm -rf ./feeds/packages/net/mosdns && cp -r -f ./feeds/smpackage/mosdns ./feeds/packages/net/mosdns

sed -i 's/192.168.1.1/192.168.100.1/g' openwrt/package/base-files/files/bin/config_generate


# 修改插件名字

 sed -i 's/"AirPlay 2 音频接收器"/"AirPlay 2"/g' `grep "AirPlay 2 音频接收器" -rl ./`
 sed -i 's/"UPnP IGD 和 PCP/NAT-PMP"/"UPnP"/g' `grep "UPnP IGD 和 PCP/NAT-PMP" -rl ./`
