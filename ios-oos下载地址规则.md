ios 需要配置plist文件
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0">
<dict>
	<key>items</key>
	<array>
		<dict>
			<key>assets</key>
			<array>
				<dict>
					<key>kind</key>
					<string>software-package</string>
					<key>url</key>
					<string>https://huliao-download.oss-cn-shanghai.aliyuncs.com/ios/huliao.ipa</string>
				</dict>
				<dict>
					<key>kind</key>
					<string>full-size-image</string>
					<key>needs-shine</key>
					<true/>
					<key>url</key>
					<string>http://huliao-download.oss-cn-shanghai.aliyuncs.com/app/ios/icon-60.png</string>
				</dict>
				<dict>
					<key>kind</key>
					<string>display-image</string>
					<key>needs-shine</key>
					<true/>
					<key>url</key>
					<string>http://huliao-download.oss-cn-shanghai.aliyuncs.com/app/ios/icon-60.png</string>
				</dict>
			</array>
			<key>metadata</key>
			<dict>
				<key>bundle-identifier</key>
				<string>com.guquan.plus</string>
				<key>bundle-version</key>
				<string>1.0.0</string>
				<key>kind</key>
				<string>software</string>
				<key>title</key>
				<string>huliao</string>
			</dict>
		</dict>
	</array>
</dict>
</plist>




ios 下载地址
（前缀规则---itms-services://?action=download-manifest&url=）
itms-services://?action=download-manifest&url=https://imdownload.oss-cn-beijing.aliyuncs.com/ios/lianquanV1.0.0.plist