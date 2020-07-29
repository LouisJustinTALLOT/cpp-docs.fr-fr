---
title: Stockage local des threads (TLS)
ms.date: 08/09/2019
helpviewer_keywords:
- multithreading [C++], Thread Local Storage
- TLS [C++]
- threading [C++], Thread Local Storage
- storing thread-specific data
- thread attribute
- Thread Local Storage [C++]
ms.assetid: 80801907-d792-45ca-b776-df0cf2e9f197
ms.openlocfilehash: f677d7382a9747df63023bd83b104a6bb3b74c1f
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87222652"
---
# <a name="thread-local-storage-tls"></a>Stockage local des threads (TLS)

Le stockage local des threads (TLS, \{i\&gt;Thread Local Storage\&lt;i\}) est une méthode où chaque thread d'un processus multithread donné peut allouer des emplacements de stockage de données propres au thread. Les données spécifiques aux threads à liaison dynamique (au moment de l’exécution) sont prises en charge par le biais de l’API TLS ([TlsAlloc](/windows/win32/api/processthreadsapi/nf-processthreadsapi-tlsalloc)). Win32 et le compilateur Microsoft C++ prennent désormais en charge les données par thread liées statiquement (au moment du chargement) en plus de l’implémentation d’API existante.

## <a name="compiler-implementation-for-tls"></a><a name="_core_compiler_implementation_for_tls"></a>Implémentation du compilateur pour TLS

**C++ 11 :**  Le **`thread_local`** spécificateur de classe de stockage est la méthode recommandée pour spécifier le stockage local des threads pour les objets et les membres de classe. Pour plus d’informations, consultez [classes de stockage (C++)](../cpp/storage-classes-cpp.md).

MSVC fournit également un attribut spécifique à Microsoft, [thread](../cpp/thread.md), en tant que modificateur de classe de stockage étendu. Utilisez le **`__declspec`** mot clé pour déclarer une **`thread`** variable. Par exemple, le code suivant déclare une variable locale de thread entière et lui affecte une valeur initiale :

```C
__declspec( thread ) int tls_i = 1;
```

## <a name="rules-and-limitations"></a>Règles et limitations

Les instructions suivantes doivent être observées au moment de déclarer des variables et des objets locaux de thread liés statiquement. Ces instructions s’appliquent à la fois à [thread](../cpp/thread.md) et à [thread_local](../cpp/storage-classes-cpp.md):

- L' **`thread`** attribut peut être appliqué uniquement aux définitions et déclarations de classe et de données. Elle ne peut pas être utilisée dans les déclarations ou les définitions de fonctions. Par exemple, le code suivant génère une erreur de compilation :

    ```C
    __declspec( thread )void func();     // This will generate an error.
    ```

- Le **`thread`** modificateur ne peut être spécifié que sur des éléments de données avec l' **`static`** extension. Cela comprend les objets de données globaux (à la fois **`static`** et **`extern`** ), les objets statiques locaux et les membres de données statiques des classes C++. Les objets de données automatiques ne peuvent pas être déclarés avec l' **`thread`** attribut. Le code suivant génère des erreurs de compilation :

    ```C
    void func1()
    {
        __declspec( thread )int tls_i;            // This will generate an error.
    }

    int func2(__declspec( thread )int tls_i )     // This will generate an error.
    {
        return tls_i;
    }
    ```

- Les déclarations et la définition d’un objet local de thread doivent toutes spécifier l' **`thread`** attribut. Par exemple, le code suivant génère une erreur :

    ```C
    #define Thread  __declspec( thread )
    extern int tls_i;        // This will generate an error, since the
    int __declspec( thread )tls_i;        // declaration and definition differ.
    ```

- L' **`thread`** attribut ne peut pas être utilisé en tant que modificateur de type. Par exemple, le code suivant génère une erreur de compilation :

    ```C
    char __declspec( thread ) *ch;        // Error
    ```

- Étant donné que la déclaration d’objets C++ qui utilisent l' **`thread`** attribut est autorisée, les deux exemples suivants sont sémantiquement équivalents :

    ```cpp
    __declspec( thread ) class B
    {
    // Code
    } BObject;  // OK--BObject is declared thread local.

    class B
    {
    // Code
    };
    __declspec( thread ) B BObject;  // OK--BObject is declared thread local.
    ```

- L’adresse d’un objet local de thread n’est pas considérée comme étant constante, et toute expression impliquant une telle adresse n’est pas considérée comme une expression constante. En C standard, l’effet est d’interdire l’utilisation de l’adresse d’une variable locale de thread comme initialiseur d’un objet ou d’un pointeur. Par exemple, le code suivant est signalé comme une erreur par le compilateur C :

    ```C
    __declspec( thread ) int tls_i;
    int *p = &tls_i;       //This will generate an error in C.
    ```

   Cette restriction ne s’applique pas en C++. Sachant que C++ prévoit l’initialisation dynamique de tous les objets, vous pouvez initialiser un objet à l’aide d’une expression qui utilise l’adresse d’une variable locale de thread. Elle est effectuée de la même manière que la construction d’objets locaux de thread. Par exemple, le code affiché précédemment ne génère pas d’erreur lorsqu’il est compilé en tant que fichier source C++. L’adresse d’une variable locale de thread est valide uniquement tant que le thread dans lequel l’adresse a été prise existe toujours.

- Le langage C standard permet l’initialisation d’un objet ou d’une variable avec une expression qui implique une référence à elle-même, mais uniquement pour les objets d’étendue non statique. Bien que C++ autorise généralement une telle initialisation dynamique d’objets avec une expression qui implique une référence à elle-même, ce type d’initialisation n’est pas autorisé avec les objets locaux de thread. Par exemple :

    ```C
    __declspec( thread )int tls_i = tls_i;                // Error in C and C++
    int j = j;                               // OK in C++, error in C
    __declspec( thread )int tls_i = sizeof( tls_i )       // Legal in C and C++
    ```

   Une **`sizeof`** expression qui comprend l’objet initialisé ne représente pas une référence à elle-même et est activée à la fois en C et en C++.

   C++ n’autorise pas l’initialisation dynamique des données de thread en raison d’éventuelles améliorations futures de la fonctionnalité de stockage local des threads.

- Sur les systèmes d’exploitation Windows antérieurs à Windows Vista, `__declspec( thread )` présente certaines limitations. Si une DLL déclare des données ou des objets en tant que `__declspec( thread )` , elle peut provoquer une erreur de protection si elle est chargée dynamiquement. Une fois la DLL chargée avec [LoadLibrary](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibraryw), elle provoque une défaillance du système chaque fois que le code fait référence aux `__declspec( thread )` données. Sachant que l'espace de variables globales d'un thread est alloué au moment de l'exécution, la taille de cet espace varie en fonction du calcul des besoins de l'application et de ceux de toutes les DLL liées statiquement. Lorsque vous utilisez `LoadLibrary` , vous ne pouvez pas étendre cet espace pour autoriser les variables locales de thread déclarées avec `__declspec( thread )` . Utilisez les API TLS, telles que [TlsAlloc](/windows/win32/api/processthreadsapi/nf-processthreadsapi-tlsalloc), dans votre dll pour allouer TLS si la dll peut être chargée avec `LoadLibrary` .

## <a name="see-also"></a>Voir aussi

[Multithreading à l'aide de C et de Win32](multithreading-with-c-and-win32.md)
