
 ## Why Add BOM

    implementation platform('com.google.cloud:libraries-bom:26.50.0')
**Add the BOM to Manage Versions**:

• By adding the BOM, you set a version for a group of related dependencies (like all Google Cloud libraries), so you don’t need to specify versions individually.

• When you add implementation platform('com.google.cloud:libraries-bom:26.50.0'), Gradle will manage and resolve the versions for all Google Cloud dependencies to be compatible with version 26.50.0 of the BOM.

Here’s how to use the BOM in your build.gradle:

dependencies {
    // Add the Google Cloud BOM
    implementation platform('com.google.cloud:libraries-bom:26.50.0')
    
    // Add Google Cloud dependencies without specifying versions
    implementation 'com.google.cloud:google-cloud-document-ai'
    implementation 'com.google.cloud:google-cloud-storage'
}
