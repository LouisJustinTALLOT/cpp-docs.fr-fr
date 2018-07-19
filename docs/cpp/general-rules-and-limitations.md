---
title: Règles générales et Limitations | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: 6c48902d-4259-4761-95d4-e421d69aa050
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 19a704036ffac974bc99d93996d083733f59d0d4
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2018
ms.locfileid: "37943892"
---
# <a name="general-rules-and-limitations"></a>Règles générales et limitations
## <a name="microsoft-specific"></a>Section spécifique à Microsoft  
  
-   Si vous déclarez une fonction ou un objet sans le **dllimport** ou **dllexport** attribut, la fonction ou l’objet ne fait pas partie de l’interface DLL. Par conséquent, la définition de la fonction ou de l'objet doit être présente dans ce module ou dans un autre module du même programme. Pour rendre la partie de fonction ou un objet de l’interface DLL, vous devez déclarer la définition de la fonction ou d’un objet dans l’autre module en tant que **dllexport**. Sinon, une erreur d'éditeur de liens est générée.  
  
     Si vous déclarez une fonction ou un objet avec le **dllexport** attribut, sa définition doit apparaître dans un module du même programme. Sinon, une erreur d'éditeur de liens est générée.  
  
-   Si un seul module de votre programme contient à la fois **dllimport** et **dllexport** déclarations pour la même fonction ou l’objet, le **dllexport** attribut est prioritaire sur le **dllimport** attribut. Toutefois, un avertissement du compilateur est généré. Exemple :  
  
    ```cpp 
    __declspec( dllimport ) int i;  
    __declspec( dllexport ) int i;   // Warning; inconsistent;  
                                     // dllexport takes precedence.  
    ```  
  
-   En C++, vous pouvez initialiser un pointeur de données local déclaré globalement ou statique avec l’adresse d’un objet de données déclaré avec le **dllimport** attribut, qui génère une erreur en C. En outre, vous pouvez initialiser un pointeur fonction local statique avec l’adresse d’une fonction déclarée avec le **dllimport** attribut. En C, ce type d'assignation définit le pointeur sur l'adresse de la conversion de code d'importation de la DLL (stub de code qui transfère un contrôle à la fonction) plutôt que l'adresse de la fonction. En C++, il définit le pointeur sur l'adresse de la fonction. Exemple :  
  
    ```cpp 
    __declspec( dllimport ) void func1( void );  
    __declspec( dllimport ) int i;  
  
    int *pi = &i;                             // Error in C  
    static void ( *pf )( void ) = &func1;     // Address of thunk in C,  
                                              // function in C++  
  
    void func2()  
    {  
       static int *pi = &i;                  // Error in C  
       static void ( *pf )( void ) = &func1; // Address of thunk in C,  
                                             // function in C++  
    }  
    ```  
  
     Toutefois, comme un programme qui inclut le **dllexport** attribut dans la déclaration d’un objet doit fournir la définition de cet objet dans le programme, vous pouvez initialiser un pointeur de fonction statique global ou local avec l’adresse d’un **dllexport** (fonction). De même, vous pouvez initialiser un pointeur de données statiques global ou local avec l’adresse d’un **dllexport** objet de données. Par exemple, le code suivant ne génère pas d'erreur en C ni en C++ :  
  
    ```cpp 
    __declspec( dllexport ) void func1( void );  
    __declspec( dllexport ) int i;  
  
    int *pi = &i;                              // Okay  
    static void ( *pf )( void ) = &func1;      // Okay  
  
    void func2()  
    {  
        static int *pi = &i;                   // Okay  
        static void ( *pf )( void ) = &func1;  // Okay  
    }  
    ```  
  
-   Si vous appliquez **dllexport** à une classe normale qui possède une classe de base qui n’est pas marquée en tant que **dllexport**, le compilateur génère l’erreur C4275.  
  
     Le compilateur génère le même avertissement si la classe de base est une spécialisation d'un modèle de classe. Pour contourner ce problème, marquez la classe de base avec **dllexport**. Le problème avec une spécialisation de modèle de classe est l’endroit où placer le **__declspec (dllexport)**; vous n’êtes pas autorisé à marquer le modèle de classe. Au lieu de cela, explicitement instancier le modèle de classe et marquez cette instanciation explicite avec **dllexport**. Exemple :  
  
    ```cpp 
    template class __declspec(dllexport) B<int>;  
    class __declspec(dllexport) D : public B<int> {  
    // ...  
    ```  
  
     Cette solution de contournement échoue si l’argument template est la classe dérivée. Exemple :  
  
    ```cpp 
    class __declspec(dllexport) D : public B<D> {  
    // ...  
    ```  
  
     Comme il s’agit d’un modèle commun avec des modèles, le compilateur a modifié la sémantique de **dllexport** lorsqu’il est appliqué à une classe qui a une ou plusieurs classes de base et lorsqu’un ou plusieurs classes de base sont une spécialisation de modèle de classe . Dans ce cas, le compilateur applique implicitement **dllexport** aux spécialisations des modèles de classe. Vous pouvez effectuer les opérations suivantes et pas obtenir un avertissement :  
  
    ```cpp 
    class __declspec(dllexport) D : public B<D> {  
    // ...  
    ```  
  
**FIN de la section spécifique à Microsoft**  
  
## <a name="see-also"></a>Voir aussi  
 [dllexport, dllimport](../cpp/dllexport-dllimport.md)