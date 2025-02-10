---
order: 100
tags: [guide]
---

# Using the template


1. **Fork the [Extension-Template](https://github.com/jonsnow32/vivid-extension-template)**  

2. **Enable GitHub Actions Go to:** 
`Settings > Actions > General > Allow all actions and reusable workflows`

3. **Set Workflow Permissions Ensure workflows have push access in your repository:**  
`Settings > Actions > General > Read and write permissions`

4. **Start Creating:** You can now create your own plugins. After pushing new code, they should automatically be built.

---


### Basic gralde config

We can compile all Client into a Kotlin class file by implementing multiple interfaces such as DataBaseClient, StreamClient, and SubtitleClient, and defining them in the Gradle extension configuration

./build.gradle.kts
```kts
vvfExtension {
  iconUrl = "your icon url"
  authors = listOf("author1", "author2")
  version = 1
  status = 1
  types = listOf("database","subtitle", "stream")
}
```


SampleClient.kt
```kt
@VVFExtension
class SampleClient : StreamClient, DatabaseClient, SubtitleClient {

}
```