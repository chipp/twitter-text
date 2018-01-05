.PHONY: clean build

RESULT_PATH=build/Build/Products

clean: 
	rm -rf "build" "result"

build: clean
	xcodebuild -scheme TwitterText -project TwitterText.xcodeproj -configuration Release -arch arm64 -arch armv7 -arch armv7s only_active_arch=no defines_module=yes -derivedDataPath "build" -sdk "iphoneos" build
	xcodebuild -scheme TwitterText -project TwitterText.xcodeproj -configuration Release -arch x86_64 only_active_arch=no defines_module=yes -derivedDataPath "build" -sdk "iphonesimulator" build

	mkdir -p "result"

	rsync -rtvu --delete "$(RESULT_PATH)/Release-iphoneos/TwitterText.framework/" "result/TwitterText.framework/"
	lipo -create -output "result/TwitterText.framework/TwitterText" "$(RESULT_PATH)/Release-iphoneos/TwitterText.framework/TwitterText" "$(RESULT_PATH)/Release-iphonesimulator/TwitterText.framework/TwitterText"

	rsync -rtvu --delete "$(RESULT_PATH)/Release-iphoneos/IFUnicodeURL.framework/" "result/IFUnicodeURL.framework/"
	lipo -create -output "result/IFUnicodeURL.framework/IFUnicodeURL" "$(RESULT_PATH)/Release-iphoneos/IFUnicodeURL.framework/IFUnicodeURL" "$(RESULT_PATH)/Release-iphonesimulator/IFUnicodeURL.framework/IFUnicodeURL"
