# jetpack-compose-google-sign-in

https://github.com/eliezerBrasilian/jetpack-compose-google-sign-in/assets/93846923/275f9a8e-24c1-4e81-ad1f-3bbe52054d06

## How to use this package

- import the package in build.gradle(module)
 
```kotlin
implementation("com.github.eliezerBrasilian:jetpack-compose-packages:v1.1.0")
```

- import the jitpack dependency in settings gradle

```kotlin
dependencyResolutionManagement {
    repositoriesMode.set(RepositoriesMode.FAIL_ON_PROJECT_REPOS)
    repositories {
        google()
        mavenCentral()
        maven { url = uri("https://jitpack.io")  } //add me please
    }
}
```

- Example of use

```kotlin

@Composable
fun MyApp(){

val clientId = "your_web_client_inside_google_cloud"

val context = LocalContext.current

val onClickGoogleSignIn = rememberGoogleSignUp(
clientId = clientId,
context = context,
onSuccess = { result ->

 Log.d(AppTag, "id:${result.id}")
 Log.d(AppTag, "email: ${result.email}" )
 Log.d(AppTag, "name: ${result.displayName}" )
},
    onError = {
Toast.makeText(context,
"Falha ao logar com Google ❌", Toast.LENGTH_SHORT).show()
})

Box(modifier = Modifier.fillMaxSize(),
contentAlignment = Alignment.Center){
  Column(verticalArrangement = Arrangement.spacedBy(10.dp)){
  Button(onClick = onClickGoogleSignIn) {
    Text(text = "Enter with Google")
   }
  } 
 }

}

```
