# Hosting

## Let's say we are configuring for sign project. Follow the below steps.

1. **Rename the project title**
 `templatecore_kmp/settings.gradle`
 set root project name as ZohoSignCoreKMP.
 
2.  **Rename the module**
`templatecore_kmp/template_core`
<span style="font-size: 14px"> E.g., zohosign_core </span>

3. **Update library module build.gradle**
`templatecore_kmp/zohosign_core/build.gradle.kts`

	a. Find and replace template_core with zohosign_core
	b. Update android library extension namespace from
	 `com.zoho.template.core` to `com.zoho.signzohosign.core`
	c. Update maven group from
	`com.zoho.group` to `com.zoho.sign`

4. **Update the package structure in commonMain**
	`templatecore_kmp/zohosign_core/src/commonMain/kotlin/`

	`com.zoho.template.core` to `com.zoho.sign.zohosign.core`
>**Note:** <span style="font-size: 14px"> Select All Directories instead of All in Current Module while renaming to make it applicable to both androidMain and iosMain source sets.</span>

5. **Update KMP Object**
`templatecore_kmp/zohosign_core/src/commonMain/kotlin/com/zoho/sign/zohosign/core/TemplateCoreKMP.kt`
Rename **TemplateCoreKMP** to **ZohoSignCoreKMP**

6. **Update oAuth helper interface**
`templatecore_kmp/zohosign_core/src/commonMain/kotlin/com/zoho/sign/zohosign/core/TemplateCoreOauthHelper.kt`

7. **Update your repository implementation class**
``templatecore_kmp/zohosign_core/src/commonMain/kotlin/com/zoho/sign/zohosign/core/data/repository/OfflineFirstTemplateCoreRepository.kt``
Rename **OfflineFirstTemplateCoreRepository** to **OfflineFirstZohoSignCoreRepository**

8. **Update your submodule repository**
`templatecore_kmp/zohosign_core/src/commonMain/kotlin/com/zoho/sign/zohosign/core/domain/repository/ModuleOneRepository.kt`
Rename **ModuleOneRepository** to **AccountsModuleRepository**

>**Note:** <span style="font-size: 14px"> If you have more modules you can do the same to all the other interfaces under the repository directory. </span>

## Now you might have the basic understanding of how this works. Let's proceed for integration to get more insights.

9. **Use the below commands to generate executables.**
*For android*
`./gradlew publishToMavenLocal`
*For iOS*
`./gradlew assembleXCFramework` 

10. Refer this documentation or integrating in your sample project. Here we have [link](https://writer.zoho.com/writer/open/uak3b68b319c727f74c9c9002b38ec5333502).

11. **Now you can try exploring with your own API's**
- Update your product's base KMPConstants `templatecore_kmp/zohosign_core/src/commonMain/kotlin/com/zoho/sign/zohosign/core/util/KMPConstants.kt`
``const val BASE_URL = "https://sign.zoho.com"``

12. **Implement your API's in KtorRemoteDataSource class and Create your dto, domain classes under the below mentioned packages.**
`templatecore_kmp/zohosign_core/src/commonMain/kotlin/com/zoho/sign/zohosign/core/data/network/KtorRemoteDataSource.kt`

*Date Transfer Objects:*
``templatecore_kmp/zohosign_core/src/commonMain/kotlin/com/zoho/sign/zohosign/core/data/network/dto/``
*Domain classes:*
`templatecore_kmp/zohosign_core/src/commonMain/kotlin/com/zoho/sign/zohosign/core/domain/model/`
*Mapper:*
`templatecore_kmp/zohosign_core/src/commonMain/kotlin/com/zoho/sign/zohosign/core/data/mapper/Mapper.kt`

13. **Create your own repository for your project under the memobile / KMP group and push the code**

#### <center><span style="color: green">Congratulations... You did it..</span>
