---
title: カスタム配置オブジェクト
seo-title: Places APIで使用するカスタムネイティブクラス。
seo-description: Places APIで使用するカスタムネイティブクラス。
translation-type: tm+mt
source-git-commit: ef3d77eba407013e1f701ed001ef9ab7b3818e07

---


# カスタム配置オブジェクト {#places-objects}

Places APIで使用されるカスタムネイティブクラスを次に示します。

## iOS

### ACPPlacesPoi

以下に定義を示します。

```text
/**
 *  @class ACPPlacesPoi
 *
 *  This class contains data that is directly correlated to the properties maintained by the Places database.
 */
@interface ACPPlacesPoi : NSObject

@property (nonatomic, strong, nullable) NSString* identifier;  ///< The identifier for the POI
@property (nonatomic, strong, nullable) NSString* name;  ///< The name of the POI
@property (nonatomic) double latitude;  ///< The latitude of the POI's center
@property (nonatomic) double longitude;  ///< The longitude of the POI's center
@property (nonatomic) NSUInteger radius;  ///< The radius of the POI
@property (nonatomic, strong, nullable) NSDictionary<NSString*, NSString*>* metaData;  ///< Dictionary containing meta data for the POI
@property (nonatomic) Boolean userIsWithin;  ///< Indicates if the device is currently inside of this POI

@end
```

