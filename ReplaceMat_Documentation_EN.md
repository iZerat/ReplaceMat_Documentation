ReplaceMat

V1.2

documentation

(Plugin for batch setting up Unreal Engine blueprint asset materials)

## Directory

1. Introduction to the Plugin .1

2. Installation method of the plugin .3

3. The various functional modules of the plugin .7

4. Functions and usage instructions of the plugin .9

1. Copy the materials from one blueprint asset to another blueprint asset .9

2. Batch match the materials that need to be replaced for the blueprint according to the rules .17

1. Common Mode .19

2. Inverse Mode .26

3. Replace Mode 30

4. Equal Mode .35

5. Shield Mode 36

3. Batch set the same material for all material slots of all mesh component in the blueprint asset 40

4. Batch set the same material for all material slots of the mesh components specified in the blueprint asset .46

## 1. Introduction to the Plugin

This plugin can achieve batch replacement of the materials of mesh components in blueprints. Its functions include batch copying the material sequence from one blueprint to another, batch matching and replacing materials in blueprints according to common rules through character matching, batch setting the same material for blueprints, and batch setting the same material for a specified component in blueprints. Moreover, these material Settings directly modify the assets and do not require running to view the results.

For example, applicable scenarios: After the project production progress reaches a certain stage, it is inevitable to encounter many subclass assets, such as those derived from adapting to different level scenarios and different storyboards, and those that need to be specifically modified. This is equivalent to dealing with various polymorphic situations. This plugin is designed to address the pain points of users in the above situations and reduce the workload of operators.

ReplaceMat V1.2

![bo_d4tecgref24c73beecag_3_241_192_1164_660_0.jpg](images/bo_d4tecgref24c73beecag_3_241_192_1164_660_0.jpg)

(The mesh components primarily include static meshes and skeletal meshes, both of which are supported by this functionality. However, the CharacterMesh0 in the blueprint of character parent class is a rather special component and is not applicable to this plugin in some cases.)

## 2. Installation method of the plugin

Place the plugin "ReplaceMat" folder under the corresponding "Plugins" folder in the Unreal Engine project directory. If there is no "Plugins" folder, you can create a new one, rename it "Plugins", and then put the "ReplaceMat" folder within the "Plugins" folder.

![bo_d4tecgref24c73beecag_4_309_677_972_200_0.jpg](images/bo_d4tecgref24c73beecag_4_309_677_972_200_0.jpg)

Start the unreal engine project and open the Plugins menu.

![bo_d4tecgref24c73beecag_4_301_1062_741_655_0.jpg](images/bo_d4tecgref24c73beecag_4_301_1062_741_655_0.jpg)

ReplaceMat V1.2

Search for "ReplaceMat" and make sure the "ReplaceMat" plugin is enabled. If it is not enabled, simply click on the radio box on the left side of the plugin to open it.

![bo_d4tecgref24c73beecag_5_297_463_1169_296_0.jpg](images/bo_d4tecgref24c73beecag_5_297_463_1169_296_0.jpg)

Right-click at any appropriate place, select Editor Utilities, and select Editor Utility blueprint.。

![bo_d4tecgref24c73beecag_5_299_1026_1169_731_0.jpg](images/bo_d4tecgref24c73beecag_5_299_1026_1169_731_0.jpg)

ReplaceMat V1.2

Create these several Editor Utility Blueprints respectively. AAU_CopyMaterial_from_BP_to_BP, AAU_MatchMaterial_in_BP, AAU_SetTh eSameMaterial_for_BP and AAU_SetTheSameMaterial_for_CP These respectively correspond to several main functions of the plugin.

![bo_d4tecgref24c73beecag_6_309_549_1164_606_0.jpg](images/bo_d4tecgref24c73beecag_6_309_549_1164_606_0.jpg)

![bo_d4tecgref24c73beecag_6_311_1238_1162_604_0.jpg](images/bo_d4tecgref24c73beecag_6_311_1238_1162_604_0.jpg)

ReplaceMat V1.2

![bo_d4tecgref24c73beecag_7_314_201_1156_597_0.jpg](images/bo_d4tecgref24c73beecag_7_314_201_1156_597_0.jpg)

![bo_d4tecgref24c73beecag_7_318_811_1149_591_0.jpg](images/bo_d4tecgref24c73beecag_7_318_811_1149_591_0.jpg)

![bo_d4tecgref24c73beecag_7_315_1508_1059_500_0.jpg](images/bo_d4tecgref24c73beecag_7_315_1508_1059_500_0.jpg)

### 3.The various functional modules of the plugin

After the plugin is installed, the user right-click on Scripted Asset in the Unreal Engine Content Browser and selects Scripted Asset Actions. In the submenu, the main functional module menus of the plugin can be seen.

![bo_d4tecgref24c73beecag_8_241_671_1168_1048_0.jpg](images/bo_d4tecgref24c73beecag_8_241_671_1168_1048_0.jpg)

They are RM Copy Material from Blueprint to Blueprint. Copy the Material in one Blueprint to another specified blueprint. RM Match Material in Blueprint. Batch match the material that needs to be replaced for the blueprint according to the rules. RM Set the Same Material for all Material

ReplaceMat V1.2 slots of all meshes in the Blueprint batch Set the Same material and RM Set the Same Material for Component Batch set the same material for all material slots of the mesh specified in the blueprint.

## 4. Functions and usage instructions of the plugin

1. Copy the materials from one blueprint asset to another blueprint asset

This function corresponds to the RM Copy Material from Blueprint to Blueprint option.

The "Source Blueprint" column is filled with the Blueprint assets of the data source, which is equivalent to the copied blueprint. The "Target Blueprint" column is filled with the blueprint assets of the set material, which is equivalent to the target blueprint. The material data will be copied from the Source Blueprint to the Target Blueprint, and the original materials in the Target Blueprint will be replaced. After all the Settings are completed, click OK, and the plugin will perform the operation.

![bo_d4tecgref24c73beecag_10_299_1349_881_523_0.jpg](images/bo_d4tecgref24c73beecag_10_299_1349_881_523_0.jpg)

There will be a pop-up prompt indicating successful execution.

![bo_d4tecgref24c73beecag_11_305_292_755_119_0.jpg](images/bo_d4tecgref24c73beecag_11_305_292_755_119_0.jpg)

If the execution fails, a pop-up window will prompt the execution failure and inform the user of the specific reason for the failure. Other functions of the plugin also have similar operation logic and prompt feedback.

![bo_d4tecgref24c73beecag_11_299_847_565_263_0.jpg](images/bo_d4tecgref24c73beecag_11_299_847_565_263_0.jpg)

For instance, here it prompts that there is no valid blueprint input. Users need to fill in valid blueprint assets. Other functions of the plugin will also have similar prompt messages.

ReplaceMat V1.2

Here are detailed examples. For instance, we have two blueprints, namely BP_Mannequin and BP_Mannequin_release. The skeletal meshes contained in these two blueprints are the same, but the materials on the skeletal meshes are different. The material of the release version is green.

![bo_d4tecgref24c73beecag_12_300_549_742_516_0.jpg](images/bo_d4tecgref24c73beecag_12_300_549_742_516_0.jpg)

Meanwhile, the material of the BP_Mannequin_release blueprint contains the "release" character for distinction.

![bo_d4tecgref24c73beecag_12_300_1319_1040_793_0.jpg](images/bo_d4tecgref24c73beecag_12_300_1319_1040_793_0.jpg)

ReplaceMat V1.2

![bo_d4tecgref24c73beecag_13_300_194_1047_792_0.jpg](images/bo_d4tecgref24c73beecag_13_300_194_1047_792_0.jpg)

Moreover, on these two blueprint assets, apart from the characters, there are also skeletal mesh of hats and bags. Their materials are one original copy and one named "release". The specific configuration follows the blueprint assets.

![bo_d4tecgref24c73beecag_13_300_1410_1039_439_0.jpg](images/bo_d4tecgref24c73beecag_13_300_1410_1039_439_0.jpg)

ReplaceMat V1.2

Suppose at this point the requirement is to set the material of BP_Mannequin to be consistent with BP_Mannequin_release, right-click on any Asset and select Scripted Asset Actions, Select RM Copy Material from Blueprint to Blueprint.

![bo_d4tecgref24c73beecag_14_299_560_1169_707_0.jpg](images/bo_d4tecgref24c73beecag_14_299_560_1169_707_0.jpg)

ReplaceMat V1.2

In the "Source Blueprint" column, fill in the Blueprint asset of the material you want to copy. In the "Target Blueprint" column, fill in the blueprint asset of the material you want to modify. After the Settings are completed, click OK.

![bo_d4tecgref24c73beecag_15_300_551_855_509_0.jpg](images/bo_d4tecgref24c73beecag_15_300_551_855_509_0.jpg)

(If you right-click on the asset and select "Source Blueprint Asset", you don't need to fill in the corresponding Blueprint in the "Source Blueprint" field. The plugin will take the selected asset as the "Source Blueprint". Conversely, if you right-click on an asset and select "Target Blueprint", you don't need to fill in the corresponding Blueprint in the "Target Blueprint" field. The plugin will use the selected asset as the "Target Blueprint".)

Subsequently, the material on the BP_Mannequin blueprint asset was modified to be the same as that on BP_Mannequin_release.

![bo_d4tecgref24c73beecag_16_296_444_1053_1234_0.jpg](images/bo_d4tecgref24c73beecag_16_296_444_1053_1234_0.jpg)

At the same time, the execution status of the plugin can also be seen in the Output Log window.

LogTemp: Display: Has been copy 14 materials.

## ReplaceMat V1.2

This is sorted overall by component number and material slot number. As long as the skeletal mesh configuration in your two blueprints is the same, you can use this function, for example, if both blueprints are subclass of a certain blueprint, or one blueprint is a subclass of the other blueprint.

The material effects in the detailed interface of a general blueprint are not updated immediately. At this time, you need to close the interface and then reopen the blueprint interface to see the replaced material effects.

ReplaceMat V1.2

## 2. Batch match the materials that need to be replaced for the blueprint according to the rules

This function corresponds to the RM Match Material in Blueprint option.

![bo_d4tecgref24c73beecag_18_299_610_1167_267_0.jpg](images/bo_d4tecgref24c73beecag_18_299_610_1167_267_0.jpg)

After clicking, you can see the detailed operation panel of this function.

![bo_d4tecgref24c73beecag_18_302_1054_849_590_0.jpg](images/bo_d4tecgref24c73beecag_18_302_1054_849_590_0.jpg)

Enter the Blueprint for which you want to modify the Material in the "Input Blueprint" field. The drop-down list "Material Match Mode" can switch the matching mode. After checking the radio box "Show Debug Message", you can see the specific situation when the plugin is running in the console. After all the Settings are completed, click OK and the plugin will perform the operation.

There are four matching modes in total, namely Common Mode, Inverse Mode, Replace Mode, Equal Mode, and Shield Mode. Each of these four modes is suitable for different operation scenarios.

![bo_d4tecgref24c73beecag_19_300_633_858_606_0.jpg](images/bo_d4tecgref24c73beecag_19_300_633_858_606_0.jpg)

To use this function, strict norms for material naming are required. For instance, underscores should be used to separate suffixes or special words.

The following are detailed examples of each mode.

## 1. Common Mode

For instance, in a certain blueprint asset, there is the following skeletal mesh, and the mesh contains the following materials. All subsequent demonstrations will be conducted using this blueprint asset.

![bo_d4tecgref24c73beecag_20_301_577_882_744_0.jpg](images/bo_d4tecgref24c73beecag_20_301_577_882_744_0.jpg)

![bo_d4tecgref24c73beecag_20_302_1329_763_585_0.jpg](images/bo_d4tecgref24c73beecag_20_302_1329_763_585_0.jpg)

![bo_d4tecgref24c73beecag_21_294_205_910_821_0.jpg](images/bo_d4tecgref24c73beecag_21_294_205_910_821_0.jpg)

Corresponding to the following material balls, there are a total of 3 skeletal mesh components and 7 material instances. Among them, 4 are named man skeletal mesh components, only 1 is named hat skeletal mesh component, and 2 are named bag skeletal mesh components.

![bo_d4tecgref24c73beecag_21_299_1467_981_630_0.jpg](images/bo_d4tecgref24c73beecag_21_299_1467_981_630_0.jpg)

ReplaceMat V1.2

Suppose at this point, it is necessary to create a shot for the A01 storyboard. To change the character to red, the materials in the blueprint need to be replaced with the following materials. These materials already have the suffix A01, and each material slot needs to correspond one-to-one. The original body material slot should be filled with body_A01. The original material slot of head needs to be filled with head_A01 and so on. First, create a child blueprint class of BP_Mannequin.

![bo_d4tecgref24c73beecag_22_299_722_1168_644_0.jpg](images/bo_d4tecgref24c73beecag_22_299_722_1168_644_0.jpg)

![bo_d4tecgref24c73beecag_22_300_1551_761_588_0.jpg](images/bo_d4tecgref24c73beecag_22_300_1551_761_588_0.jpg)

Rename the newly created asset by adding the suffix "A01".

![bo_d4tecgref24c73beecag_23_302_288_226_344_0.jpg](images/bo_d4tecgref24c73beecag_23_302_288_226_344_0.jpg)

For newly created sub-blueprints, it is recommended to click on the "Compile" button below in the blueprint interface, even if the system does not prompt to Compile. This is because not doing so may affect the parent blueprint when modifying the sub-blueprint.

Compile :

Then select all the materials with the A01 suffix, right-click and select Scripted Asset Actions, and select RM Match Material in Blueprint.

![bo_d4tecgref24c73beecag_23_299_1424_711_709_0.jpg](images/bo_d4tecgref24c73beecag_23_299_1424_711_709_0.jpg)

Enter the Blueprint assets for which you want to replace the Material in the "Input Blueprint" field. The Material Match Mode remains the default "Common". The two items "Shield Characters 0" and "Shield Characters 1" are for the Shield mode. Here, we can just ignore them. After completing the Settings, click "OK".

![bo_d4tecgref24c73beecag_24_302_635_860_516_0.jpg](images/bo_d4tecgref24c73beecag_24_302_635_860_516_0.jpg)

(The "Show Debug Message" can be seen by dragging the window down. The default window size cannot display all the content)

After the plugin is executed, the materials in the blueprint are matched and replaced.

![bo_d4tecgref24c73beecag_25_300_373_661_946_0.jpg](images/bo_d4tecgref24c73beecag_25_300_373_661_946_0.jpg)

![bo_d4tecgref24c73beecag_25_305_1327_1040_781_0.jpg](images/bo_d4tecgref24c73beecag_25_305_1327_1040_781_0.jpg)

ReplaceMatV1.2

![bo_d4tecgref24c73beecag_26_298_203_1046_984_0.jpg](images/bo_d4tecgref24c73beecag_26_298_203_1046_984_0.jpg)

At the same time, the execution status of the plugin can also be seen in the Output Log window.

![bo_d4tecgref24c73beecag_26_299_1454_1040_135_0.jpg](images/bo_d4tecgref24c73beecag_26_299_1454_1040_135_0.jpg)

## 2. Inverse Mode

If the materials of the mesh in the blueprint are set with suffixes, for example, the suffixes of the following materials are A01, and then there is a batch of materials without the A01 suffix, we want to replace the materials in the blueprint back to the version without the suffix.

![bo_d4tecgref24c73beecag_27_301_669_1042_783_0.jpg](images/bo_d4tecgref24c73beecag_27_301_669_1042_783_0.jpg)

ReplaceMat V1.2

![bo_d4tecgref24c73beecag_28_242_193_1166_747_0.jpg](images/bo_d4tecgref24c73beecag_28_242_193_1166_747_0.jpg)

Select all of these materials without suffixes, right-click and select

Scripted Asset Actions, then select "RM Match Material in Blueprint".

![bo_d4tecgref24c73beecag_28_300_1122_891_933_0.jpg](images/bo_d4tecgref24c73beecag_28_300_1122_891_933_0.jpg)

ReplaceMat V1.2

In the "Input Blueprint" field, fill in the blueprint you want to replace materials. In the "Material Match Mode", select the "Inverse mode". After completing the Settings, click OK.

![bo_d4tecgref24c73beecag_29_300_464_945_512_0.jpg](images/bo_d4tecgref24c73beecag_29_300_464_945_512_0.jpg)

Then the materials in the blueprint asset were matched and replaced back with those without suffixes.

![bo_d4tecgref24c73beecag_29_299_1239_617_866_0.jpg](images/bo_d4tecgref24c73beecag_29_299_1239_617_866_0.jpg)

## ReplaceMat V1.2

![bo_d4tecgref24c73beecag_30_293_196_859_1440_0.jpg](images/bo_d4tecgref24c73beecag_30_293_196_859_1440_0.jpg)

At the same time, the execution status of the plugin can also be seen in the Output Log window.

![bo_d4tecgref24c73beecag_30_294_1886_1036_140_0.jpg](images/bo_d4tecgref24c73beecag_30_294_1886_1036_140_0.jpg)

## 3. Replace Mode

Suppose the materials of the skeletal mesh in the blueprint asset are the following ones with the A01 suffix. We want to replace them with those with the B03 suffix, that is, the blue ones in the following picture.

![bo_d4tecgref24c73beecag_31_302_579_1048_792_0.jpg](images/bo_d4tecgref24c73beecag_31_302_579_1048_792_0.jpg)

![bo_d4tecgref24c73beecag_32_296_193_1172_748_0.jpg](images/bo_d4tecgref24c73beecag_32_296_193_1172_748_0.jpg)

First of all, a copy of the original blueprint asset can be made.

![bo_d4tecgref24c73beecag_32_302_1116_548_809_0.jpg](images/bo_d4tecgref24c73beecag_32_302_1116_548_809_0.jpg)

Rename the suffix to B03.

![bo_d4tecgref24c73beecag_33_300_287_281_434_0.jpg](images/bo_d4tecgref24c73beecag_33_300_287_281_434_0.jpg)

Select all the materials with the suffix B03, right-click and select Scripted Asset Actions, then select RM Match Material in Blueprint.

![bo_d4tecgref24c73beecag_33_299_979_975_1128_0.jpg](images/bo_d4tecgref24c73beecag_33_299_979_975_1128_0.jpg)

Fill in the Blueprint you want to modify in the Input Blueprint field. Select the Replace Mode in Material Match Mode. After completing the Settings, click OK.

![bo_d4tecgref24c73beecag_34_300_468_703_414_0.jpg](images/bo_d4tecgref24c73beecag_34_300_468_703_414_0.jpg)

After the plugin is executed, the materials in the blueprint assets are matched and replaced with those with the suffix B03.

![bo_d4tecgref24c73beecag_34_300_1062_735_1049_0.jpg](images/bo_d4tecgref24c73beecag_34_300_1062_735_1049_0.jpg)

ReplaceMat V1.2

![bo_d4tecgref24c73beecag_35_298_205_898_674_0.jpg](images/bo_d4tecgref24c73beecag_35_298_205_898_674_0.jpg)

![bo_d4tecgref24c73beecag_35_297_908_916_851_0.jpg](images/bo_d4tecgref24c73beecag_35_297_908_916_851_0.jpg)

At the same time, the execution status of the plugin can also be seen in the Output Log window.

![bo_d4tecgref24c73beecag_35_294_1931_1017_143_0.jpg](images/bo_d4tecgref24c73beecag_35_294_1931_1017_143_0.jpg)

ReplaceMat V1.2

## 4. Equal Mode

The equality pattern is relatively simple. It matches materials with exactly the same material name and replaces them. It's like the names are the same, but the materials don't have to be the same material. For example, it could be two different materials with the same name on different paths.

![bo_d4tecgref24c73beecag_36_301_759_855_517_0.jpg](images/bo_d4tecgref24c73beecag_36_301_759_855_517_0.jpg)

At the same time, the execution status of the plugin can also be seen in the Output Log window.

Display:

LogTemp: Display: Match Mode is Equal.

tal of 7 mesh slot materials.

LogTemp: Display: Successful matched and replaced 7 materials.

## 5. Shield Mode

The shield mode is rather complex and is used to handle situations where the material names do not match so well. For instance, in the name of the material that needs to be replaced, the feature character is in the middle, not the suffix. For example, the "release" character is in the middle of the entire name. We need to ignore the "release" character in the middle when matching.

![bo_d4tecgref24c73beecag_37_299_857_1169_706_0.jpg](images/bo_d4tecgref24c73beecag_37_299_857_1169_706_0.jpg)

ReplaceMat V1.2

Select all these materials with the "release" character in the middle, right-click and select Scripted Asset behavior, then select "RM Match Material in Blueprint".

![bo_d4tecgref24c73beecag_38_299_457_815_915_0.jpg](images/bo_d4tecgref24c73beecag_38_299_457_815_915_0.jpg)

In the "Input Blueprint" field, fill in the blueprint you want to modify. In the "Material Match Mode", select the "Shield mode", and in the "Shield Characters" below, fill in the characters you want to ignore. It can be filled in either Shield Characters 0 or Shield Characters 1. Here, it is designed so that users can trim two segments of characters, so two slots are reserved.

ReplaceMatV1.2

In the legend, fill "release" in the "Shield Characters 0" column. After all Settings are completed, There is no need to fill in the underline before "release". When the plugin is executed, it will automatically complete the underline. This also means that the material naming convention uses underscores to separate each word. click "OK" and the plugin will perform the operation.

![bo_d4tecgref24c73beecag_39_360_723_710_425_0.jpg](images/bo_d4tecgref24c73beecag_39_360_723_710_425_0.jpg)

After the plugin is executed, the materials in the blueprint assets are matched and replaced.

![bo_d4tecgref24c73beecag_39_358_1411_472_697_0.jpg](images/bo_d4tecgref24c73beecag_39_358_1411_472_697_0.jpg)

ReplaceMat V1.2

![bo_d4tecgref24c73beecag_40_299_205_897_1521_0.jpg](images/bo_d4tecgref24c73beecag_40_299_205_897_1521_0.jpg)

At the same time, the execution status of the plugin can also be seen in the Output Log window.

![bo_d4tecgref24c73beecag_40_293_1976_1037_135_0.jpg](images/bo_d4tecgref24c73beecag_40_293_1976_1037_135_0.jpg)

ReplaceMat V1.2

## 3. Batch set the same material for all material slots of all mesh component in the blueprint asset

This function corresponds to the "RM Set the Same Material for Blueprint" option.

![bo_d4tecgref24c73beecag_41_296_613_1172_260_0.jpg](images/bo_d4tecgref24c73beecag_41_296_613_1172_260_0.jpg)

After clicking, you can see the detailed operation panel of this function.

![bo_d4tecgref24c73beecag_41_299_1050_863_514_0.jpg](images/bo_d4tecgref24c73beecag_41_299_1050_863_514_0.jpg)

In the "Input Blueprint" field, fill in the blueprint asset of the material you want to replace. In the "Input Material" field, fill in the material you want to replace to. Finally, click "OK" and the plugin will perform the operation.

ReplaceMat V1.2

The following is an operation example. Suppose there is a blueprint asset, a material of an ice cube.

![bo_d4tecgref24c73beecag_42_307_378_618_466_0.jpg](images/bo_d4tecgref24c73beecag_42_307_378_618_466_0.jpg)

Right-click on the Asset, select Scripted Asset Actions, and select "RM Set the Same Material for Blueprint".

![bo_d4tecgref24c73beecag_42_309_1111_733_430_0.jpg](images/bo_d4tecgref24c73beecag_42_309_1111_733_430_0.jpg)

In the "Input Blueprint" column of the Input window, fill in the above-mentioned blueprint assets. In the "Input Material" column, fill in the ice cube material. After the Settings are completed, click OK.

ReplaceMat V1.2

![bo_d4tecgref24c73beecag_43_309_192_780_445_0.jpg](images/bo_d4tecgref24c73beecag_43_309_192_780_445_0.jpg)

(If you right-click on the asset and select the Blueprint asset, you don't need to fill in the target Blueprint in the Input Blueprint field. The plugin will use the selected asset as the Input Blueprint. Conversely, if you right-click on the asset and select the Material asset, then you don't need to fill in the target material in the Input Material field. The plugin will take the selected asset as Input material.)

After the plugin is executed, the ice cube material is filled into all the material slots in this blueprint.

![bo_d4tecgref24c73beecag_43_308_1407_548_705_0.jpg](images/bo_d4tecgref24c73beecag_43_308_1407_548_705_0.jpg)

ReplaceMat V1.2

![bo_d4tecgref24c73beecag_44_300_195_936_1566_0.jpg](images/bo_d4tecgref24c73beecag_44_300_195_936_1566_0.jpg)

At the same time, the execution status of the plugin can also be seen in the Output Log window.

LogTemp: Display: ---------- Replace Mat Plugins Message -

LogTemp: Display: Has been set 7 materials in 1 Blueprint.

ReplaceMat V1.2

This function not only enables operations on individual blueprint asset but also allows for batch operations on multiple blueprint assets simultaneously.

When operating, select multiple blueprint assets for which you want to replace the material. Right-click and select Scripted Asset Actions, then select "RM Set the Same Material for Blueprint".

If the several blueprint assets that are operated on by the plugin are child blueprint, it is recommended to open each of them in the editing panel and click Compile. Otherwise, performing the plugin operation will affect the parent class blueprint assets.

![bo_d4tecgref24c73beecag_45_299_1252_963_537_0.jpg](images/bo_d4tecgref24c73beecag_45_299_1252_963_537_0.jpg)

Leave the "Input Blueprint" field blank to indicate batch operations on multiple blueprint assets. If a blueprint asset is filled in the "Input Blueprint" field, it will be prioritized for individual operations on a certain

blueprint asset. Fill in the material you want to replace it with in the "Input Material" field. After the Settings are completed, click OK.

![bo_d4tecgref24c73beecag_46_300_374_861_518_0.jpg](images/bo_d4tecgref24c73beecag_46_300_374_861_518_0.jpg)

After the plugin is executed, all the blueprint assets that have been multi-selected have their materials replaced.

![bo_d4tecgref24c73beecag_46_300_1158_988_468_0.jpg](images/bo_d4tecgref24c73beecag_46_300_1158_988_468_0.jpg)

At the same time, the execution status of the plugin can also be seen in the Output Log window.

LogTemp: Display: ---------- Replace Mat Plugins Message

LogTemp: Display: Has been set 21 materials in 3 Blueprints.

ReplaceMat V1.2

## 4. Batch set the same material for all material slots of the mesh components specified in the blueprint asset

This function corresponds to the option "RM Set the Same Material for Component".

![bo_d4tecgref24c73beecag_47_297_617_1170_255_0.jpg](images/bo_d4tecgref24c73beecag_47_297_617_1170_255_0.jpg)

After clicking, you can see the detailed operation panel of this function.

![bo_d4tecgref24c73beecag_47_309_1059_866_540_0.jpg](images/bo_d4tecgref24c73beecag_47_309_1059_866_540_0.jpg)

In the "Input Blueprint" field, fill in the blueprint asset of the Material you want to replace. In the "Component Name" field, fill in the user-defined component name of the mesh component for which you want to replace the material. In the "Input Material" field, fill in the material asset you want to modify. Finally, click OK and the plugin will perform the operation.

ReplaceMat V1.2

The plugin will query whether there is a suitable blueprint mesh Component based on the Component Name entered by the user.

(If you right-click on the asset and select the Blueprint asset, you don't need to fill in the target Blueprint in the Input Blueprint field. The plugin will use the selected asset as the Input Blueprint. Conversely, if you right-click on the asset and select the Material asset, then you don't need to fill in the target material in the Input Material field. The plugin will take the selected asset as Input material.)

Here is an example. For instance, I only want all the material slots in the bag skeleton mesh component of this blueprint asset to be set to ice material, while the materials of the body and the hat remain unchanged.

![bo_d4tecgref24c73beecag_49_300_206_869_1111_0.jpg](images/bo_d4tecgref24c73beecag_49_300_206_869_1111_0.jpg)

![bo_d4tecgref24c73beecag_49_305_1339_1047_540_0.jpg](images/bo_d4tecgref24c73beecag_49_305_1339_1047_540_0.jpg)

The name of the skeletal mesh component of the backpack is "bag".

![bo_d4tecgref24c73beecag_50_300_299_1041_453_0.jpg](images/bo_d4tecgref24c73beecag_50_300_299_1041_453_0.jpg)

Right-click on the Asset, select Scripted Asset Actions, and select "RM

Set the Same Material for Component".

![bo_d4tecgref24c73beecag_50_297_1021_1173_828_0.jpg](images/bo_d4tecgref24c73beecag_50_297_1021_1173_828_0.jpg)

Fill in the blueprint asset of the material you want to replace in the "Input Blueprint" field, fill in the Component Name "bag" of the material

ReplaceMat V1.2 you want to replace in the "Component Name" field, and fill in the ice cube material in the "Input Material" field. After all the Settings are completed, click OK.

![bo_d4tecgref24c73beecag_51_300_465_911_507_0.jpg](images/bo_d4tecgref24c73beecag_51_300_465_911_507_0.jpg)

After the plugin is executed, it can be seen that the material of only the grid body component of the backpack has been replaced to the material of ice block.

![bo_d4tecgref24c73beecag_51_300_1338_608_795_0.jpg](images/bo_d4tecgref24c73beecag_51_300_1338_608_795_0.jpg)

ReplaceMat V1.2

![bo_d4tecgref24c73beecag_52_298_203_1050_553_0.jpg](images/bo_d4tecgref24c73beecag_52_298_203_1050_553_0.jpg)

At the same time, the execution status of the plugin can also be seen in the Output Log window.

LogTempt Display: Replace Mat Plugins Message

LogTemp: Display: Total of 3 conform to the name component.

LogTemp: Display: Successful set 2 materials.

This function is similar to the above "RM Set the Same Material for Blueprint", and it can also perform batch operations on multiple blueprint assets simultaneously.

Suppose we need to set the hat mesh component in the following three blueprint assets to red material. You need to right-click, select Scripted Asset Actions, and select "RM Set the Same Material for Component".

If the several blueprint assets that are operated on by the plugin are child blueprint, it is recommended to open each of them in the editing panel and click Compile. Otherwise, performing the plugin operation will affect the parent class blueprint assets.

![bo_d4tecgref24c73beecag_53_297_457_1173_743_0.jpg](images/bo_d4tecgref24c73beecag_53_297_457_1173_743_0.jpg)

Also leave the Input Blueprint field blank, fill "bag" in the Component Name field, and fill red material in the Input Material field. After the Settings are completed, click OK.

![bo_d4tecgref24c73beecag_53_299_1546_857_511_0.jpg](images/bo_d4tecgref24c73beecag_53_299_1546_857_511_0.jpg)

After the plugin is executed, you can see that the hat mesh components in all the blueprint assets selected by multiple selections have been set to red material.

![bo_d4tecgref24c73beecag_54_300_461_1003_431_0.jpg](images/bo_d4tecgref24c73beecag_54_300_461_1003_431_0.jpg)

At the same time, the execution status of the plugin can also be seen in the Output Log window.

LogTemp: Display: ---------- Replace Mat Plugins Message

LogTemp: Display: Total of 9 conform to the name component.

LogTemp: Display: Successful set 3 materials.