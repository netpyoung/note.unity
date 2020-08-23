Addressable Asset System (AAS)
=============================


로컬
로컬리모트
- BuildTarget
    - LocalBuildPath
    - LocalLoadPath
    - RemoteBuildPath
    - RemoteLoadPath


DEFINE SYMBOL : ADDRESSABLES_LOG_ALL 

|         |                          |
|---------|--------------------------|
| Fast    | AssetDataBase => load => |
| Virtual |                          |
| Packed  |                          |

|          | Fast | Virtual | Packed |
|----------|------|---------|--------|
| 프로파일 | x    | o       |        |
==============================

```
AddressableAssetsData/
    AssetGroups/
        Schemas/
            Built In Data_PlayerDataGroupSchema.asset          // PlayerDataGroupSchema
            Default Local Group_BundledAssetGroupSchema.asset  // BundledAssetGroupSchema
            Default Local Group_ContentUpdateGroupSchema.asset // ContentUpdateGroupSchema
        Built In Data.asset                                    // AddressableAssetGroup
        Default Local Group.asset                              // AddressableAssetGroup
    AssetGroupTemplates/
        Packed Assets.asset                                    // AddressableAssetGroupTemplate
    DataBuilders/
        BuildScriptFastMode.asset                             // BuildScriptFastMode : BuildScriptBase
        BuildScriptPackedMode.asset
        BuildScriptPackedPlayMode.asset
        BuildScriptVirtualMode.asset
    AddressableAssetSettings.asset                            //AddressableAssetSettings.cs
    DefaultObject.asset
  
    <Platform>/
        addressables_content_state.bin

```

AddressableAssetSettings.asset // => Manage Profiles

|                 |                                                                        |
|-----------------|------------------------------------------------------------------------|
| Profile Name    | Default                                                                |
| BuildTarget     | [UnityEditor.EditorUserBuildSettings.activeBuildTarget]                |
| LocalBuildPath  | [UnityEngine.AddressableAssets.Addressables.BuildPath]/[BuildTarget]   |
| LocalLoadPath   | {UnityEngine.AddressableAssets.Addressables.RuntimePath}/[BuildTarget] |
| RemoteBuildPath | ServerData/[BuildTarget]                                               |
| RemoteLoadPath  | http://localhost/[BuildTarget]                                         |

``` tree
/Library/com.unity.addressables/StreamingAssetsCopy/
    Windows/
      addressables_content_state.bin
    aa/
      Windows/
        catalog.json
        link.xml
        settings.json
        StandaloneWindows/
            blabla.bundle
``` 
```
/ServerData/
    StandaloneWindows/
      [name]_assets_all_####.bundle
      defaultlocalgroup_assets_all_###.bundle
      defaultlocalgroup_unitybuiltinshaders_###.bundle
```
BuildTarget - https://docs.unity3d.com/ScriptReference/BuildTarget.html
Windows - https://docs.unity3d.com/ScriptReference/OperatingSystemFamily.html


`addressables_content_state.bin`
contains hash and dependency information for every StaticContent asset group in the Addressables system. You should store this file where you can easily retrieve it.

------------------------------




Window > Asset Management > Addressables > Groups > Create Addressables Settings

Built In Data
  - EditorSeceneList | Scenes In Build
  - Resources        | */Resources/
Default Local Group(Default)
  - ... 
  
AssetReferance

https://docs.unity3d.com/Packages/com.unity.addressables@0.4/api/UnityEngine.AddressableAssets.AssetReference.html

public Hash128 RuntimeKey { get; }


초기화
Addressables - Resource Locator - Content Catalog(json)
Resource Manager - Sample Provider ...N


``` plantuml
User -> Addressables : address
Addressables -> ResourceManager : resource location
User <- ResourceManager : Async
```

``` csharp
AddressableAssetEntry entry = GetAddressableAssetEntry(o);
if (entry != null)
{
    entry.address = id;
}


AddressableAssetSettings aaSettings = AddressableAssetSettingsDefaultObject.Settings;
 
AddressableAssetEntry entry = null;
string guid = string.Empty;
long localID = 0;
string path;

bool foundAsset = AssetDatabase.TryGetGUIDAndLocalFileIdentifier(o, out guid, out localID);
path = AssetDatabase.GUIDToAssetPath(guid);

if (foundAsset && (path.ToLower().Contains("assets")))
{
    if (aaSettings != null)
    {
        entry = aaSettings.FindAssetEntry(guid);
    }
}

if (entry != null)
{
    return entry;
}
 
```
 
 ``` csharp
 [MenuItem("Tools/Refresh Addressables")]
public static void RefreshAddressables()
{
    var settings = AddressableAssetSettingsDefaultObject.Settings;
    var group = settings.DefaultGroup;
    var guids = AssetDatabase.FindAssets("t:ScriptableObject", new[] {"Assets/ScriptableObjects"});
 
    var entriesAdded = new List<AddressableAssetEntry>();
    for (int i = 0; i < guids.Length; i++)
    {
        var entry = settings.CreateOrMoveEntry(guids[i], group, readOnly: false, postEvent: false));
        entry.address = AssetDatabase.GUIDToAssetPath(guids[i]);
        entry.labels.Add("MyLabel");

        entriesAdded.Add(entry);
    }

    settings.SetDirty(AddressableAssetSettings.ModificationEvent.EntryMoved, entriesAdded, true);
}
 ```


 ``` csharp
 Addressables.LoadAsset<>("") => obj
 Addressables.ReleaseAsset<>(obj)

 Addressables.Instantiate<> => obj
 Addressables.ReleaseInstance<>(obj)
 
 

// 인스펙터
AssetReference assetRefMember;

 assetRefMember.LoadAsset<> => obj
 assetRefMember.ReleaseAsset<>(obj)

 assetRefMember.Instantiate<> => obj
 assetRefMember.ReleaseInstance<>(obj)
 ```

``` csharp
var entry = settings.CreateOrMoveEntry(guid, group, readOnly, postEvent);
entry.address = AssetDatabase.GUIDToAssetPath(guid);
entry.labels.Add("MyLabel");
```

```
AddressableAssetSettings.asset
  - Catalog
    - Build Remote Catalog [X]
  - General/
    - Send Profiler Events
    - Build Remote Catalog
    - Profiles
      - BuildTarget
      - LocalBuildPath
      - LocalLoadPath
      - RemoteBuildPath
      - RemoteLoadPath
DefaultObject.asset
Group.asset
  - PlayerVersionOverload
  - BuildPath
  - LoadPath
```

Path/
  <Platform>/
    catalog_...hash
    catalog_...json
    blabla.bundle

BuildPath
LoadPath
ProviderType

PlayMode

=========
``` csharp
[AssetReferenceTypeRestriction(typeof(GameObject))]
[AssetReferenceLabelRestriction("SampleLabel")]
```

=====================
호스팅




=============etc
Code coverage - package