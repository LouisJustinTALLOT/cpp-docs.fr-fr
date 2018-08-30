---
title: (TLS) de stockage Local des threads | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- multithreading [C++], Thread Local Storage
- TLS [C++]
- threading [C++], Thread Local Storage
- storing thread-specific data
- thread attribute
- Thread Local Storage [C++]
ms.assetid: 80801907-d792-45ca-b776-df0cf2e9f197
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e5720fcbc5c52936a0e29c2ccf0847309636b5f2
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/29/2018
ms.locfileid: "43211855"
---
# <a name="thread-local-storage-tls"></a>Stockage local des threads (TLS)
Le stockage local des threads (TLS, {i>Thread Local Storage<i}) est une méthode où chaque thread d'un processus multithread donné peut allouer des emplacements de stockage de données propres au thread. Dynamiquement les données propres au thread (exécution) sont pris en charge par le biais de l’API TLS ([TlsAlloc](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-tlsalloc).  Win32 et le compilateur Visual C++ prennent désormais en charge les données par thread liées statiquement (au moment du chargement) en plus de l'implémentation existante des API.  
  
##  <a name="_core_compiler_implementation_for_tls"></a> Implémentation du compilateur pour TLS  
 
**C ++ 11 :** le `thread_local` spécificateur de classe de stockage est la méthode recommandée pour spécifier le stockage local des threads pour les objets et membres de classe. Pour plus d’informations, consultez [classes de stockage (C++)](../cpp/storage-classes-cpp.md).  
  
Visual C++ fournit également un attribut spécifique à Microsoft, [thread](../cpp/thread.md), en tant que modificateur de classe de stockage étendu. Utilisez le **__declspec** mot clé pour déclarer un **thread** variable. Par exemple, le code suivant déclare une variable locale de thread entière et lui affecte une valeur initiale :  
  
```  
__declspec( thread ) int tls_i = 1;  
```  
  
## <a name="rules-and-limitations"></a>Règles et limitations  
 
Les instructions suivantes doivent être observées au moment de déclarer des variables et des objets locaux de thread liés statiquement. Ces instructions s’appliquent à [thread](../cpp/thread.md)et pour l’essentiel de [thread_local](../cpp/storage-classes-cpp.md):  
  
- Le **thread** attribut peut être appliqué uniquement aux déclarations de classe et les données et les définitions. Il ne peut pas être utilisé avec des définitions ou des déclarations de fonction. Par exemple, le code suivant génère une erreur de compilation :  
  
    ```  
    __declspec( thread )void func();     // This will generate an error.  
    ```  
  
- Le **thread** modificateur peut être spécifié uniquement sur les éléments de données avec **statique** étendue. Cela inclut les objets de données globaux (à la fois **statique** et **extern**), les objets statiques locaux et les membres de données statiques des classes C++. Objets de données automatiques ne peuvent pas être déclarés avec le **thread** attribut. Le code suivant génère des erreurs de compilation :  
  
    ```  
    void func1()  
    {  
        __declspec( thread )int tls_i;            // This will generate an error.  
    }  
  
    int func2(__declspec( thread )int tls_i )    // This will generate an error.  
    {  
        return tls_i;  
    }  
    ```  
  
- Les déclarations et la définition d’un thread objet local doit spécifier le **thread** attribut. Par exemple, le code suivant génère une erreur :  
  
    ```  
    #define Thread  __declspec( thread )  
    extern int tls_i;        // This will generate an error, since the  
    int __declspec( thread )tls_i;        // declaration and definition differ.  
    ```  
  
- Le **thread** attribut ne peut pas être utilisé comme un modificateur de type. Par exemple, le code suivant génère une erreur de compilation :  
  
    ```  
    char __declspec( thread ) *ch;        // Error  
    ```  
  
- Étant donné que la déclaration d’objets C++ qui utilisent le **thread** attribut est autorisé, les deux exemples suivants sont sémantiquement équivalentes :  
  
    ```  
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
  
- L’adresse d’un objet local de thread n’est pas considérée comme étant constante, et toute expression impliquant une telle adresse n’est pas considérée comme une expression constante. En C standard, la conséquence de ceci est l'interdiction d'utiliser l'adresse d'une variable locale de thread comme initialiseur d'un objet ou pointeur. Par exemple, le code suivant est signalé comme une erreur par le compilateur C :  
  
    ```  
    __declspec( thread )int tls_i;  
    int *p = &tls_i;       //This will generate an error in C.  
    ```  
  
     Cette restriction ne s'applique pas en C++. Sachant que C++ prévoit l'initialisation dynamique de tous les objets, vous pouvez initialiser un objet à l'aide d'une expression qui utilise l'adresse d'une variable locale de thread. Il s'agit de la même procédure que pour construire des objets locaux de thread. Par exemple, le code présenté plus haut ne génère pas d'erreur quand il est compilé en tant que fichier source C++. Notez que l'adresse d'une variable locale de thread est valide aussi longtemps qu'existe le thread d'où l'adresse a été extraite.  
  
- Le langage C standard prévoit l'initialisation d'un objet ou d'une variable à l'aide d'une expression impliquant une auto-référence, mais uniquement pour les objets d'étendue non statique. Même si C++ prévoit généralement l'initialisation dynamique d'objets à l'aide d'une expression impliquant une auto-référence, ce type d'initialisation n'est pas permis avec les objets locaux de thread. Exemple :  
  
    ```  
    __declspec( thread )int tls_i = tls_i;                // Error in C and C++   
    int j = j;                               // OK in C++, error in C  
    __declspec( thread )int tls_i = sizeof( tls_i )       // Legal in C and C++  
    ```  
  
     Notez qu'une expression `sizeof` qui inclut l'objet initialisé ne représente pas une auto-référence et qu'elle est autorisée aussi bien en C qu'en C++.  
  
     C++ n’autorise pas l’initialisation dynamique des données de thread en raison des possibles futures améliorations dont pourrait bénéficier la fonctionnalité de stockage local des threads.  
  
- Sur les systèmes d’exploitation Windows avant Windows Vista, `__declspec`(thread) présente certaines limitations. Si une DLL déclare des données ou un objet en tant que `__declspec`( thread ), elle peut provoquer une erreur de protection si elle est chargée de façon dynamique. Une fois que la DLL est chargée avec [LoadLibrary](https://msdn.microsoft.com/library/windows/desktop/ms684175), provoque une défaillance système chaque fois que le code fait référence le `__declspec`données (thread). Sachant que l’espace de variables globales d’un thread est alloué au moment de l’exécution, la taille de cet espace varie en fonction du calcul des besoins de l’application et de ceux de toutes les DLL liées statiquement. Quand vous utilisez `LoadLibrary`, vous ne pouvez pas étendre cet espace pour tenir compte des variables locales de thread déclarées avec `__declspec`( thread ). Utiliser les API TLS, telles que [TlsAlloc](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-tlsalloc), dans votre DLL pour allouer TLS si la DLL peut être chargée par `LoadLibrary`.  
  
## <a name="see-also"></a>Voir aussi  
 
[Multithreading à l’aide de C et de Win32](multithreading-with-c-and-win32.md)   