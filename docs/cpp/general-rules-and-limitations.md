---
title: Règles générales et limitations
ms.date: 11/04/2016
ms.assetid: 6c48902d-4259-4761-95d4-e421d69aa050
ms.openlocfilehash: 3bd8956b08d3e5f2109c5574802a3a8a72fba537
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857526"
---
# <a name="general-rules-and-limitations"></a>Règles générales et limitations

**Section spécifique de Microsoft**

- Si vous déclarez une fonction ou un objet sans l’attribut **DllImport** ou **dllexport** , la fonction ou l’objet n’est pas considéré comme faisant partie de l’interface dll. Par conséquent, la définition de la fonction ou de l'objet doit être présente dans ce module ou dans un autre module du même programme. Pour que la fonction ou l’objet fasse partie de l’interface DLL, vous devez déclarer la définition de la fonction ou de l’objet dans l’autre module en tant que **dllexport**. Sinon, une erreur d'éditeur de liens est générée.

   Si vous déclarez une fonction ou un objet avec l’attribut **dllexport** , sa définition doit apparaître dans un module du même programme. Sinon, une erreur d'éditeur de liens est générée.

- Si un seul module de votre programme contient des déclarations **DllImport** et **dllexport** pour la même fonction ou le même objet, l’attribut **dllexport** est prioritaire sur l’attribut **DllImport** . Toutefois, un avertissement du compilateur est généré. Par exemple :

    ```cpp
    __declspec( dllimport ) int i;
    __declspec( dllexport ) int i;   // Warning; inconsistent;
                                     // dllexport takes precedence.
    ```

- Dans C++, vous pouvez initialiser un pointeur de données local déclaré ou statique globalement, ou avec l’adresse d’un objet de données déclaré avec l’attribut **DllImport** , qui génère une erreur en C. En outre, vous pouvez initialiser un pointeur de fonction locale statique avec l’adresse d’une fonction déclarée avec l’attribut **DllImport** . En C, ce type d'assignation définit le pointeur sur l'adresse de la conversion de code d'importation de la DLL (stub de code qui transfère un contrôle à la fonction) plutôt que l'adresse de la fonction. En C++, il définit le pointeur sur l'adresse de la fonction. Par exemple :

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

   Toutefois, étant donné qu’un programme qui comprend l’attribut **dllexport** dans la déclaration d’un objet doit fournir la définition de cet objet quelque part dans le programme, vous pouvez initialiser un pointeur fonction statique global ou local avec l’adresse d’une fonction **dllexport** . De même, vous pouvez initialiser un pointeur de données statiques global ou local avec l’adresse d’un objet de données **dllexport** . Par exemple, le code suivant ne génère pas d'erreur en C ni en C++ :

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

- Si vous appliquez **dllexport** à une classe normale qui a une classe de base qui n’est pas marquée en tant que **dllexport**, le compilateur génère C4275.

   Le compilateur génère le même avertissement si la classe de base est une spécialisation d'un modèle de classe. Pour contourner ce contournement, marquez la classe de base avec **dllexport**. Le problème avec une spécialisation d’un modèle de classe est l’emplacement où placer le **__declspec (dllexport)** ; vous n’êtes pas autorisé à marquer le modèle de classe. Au lieu de cela, instanciez explicitement le modèle de classe et marquez cette instanciation explicite avec **dllexport**. Par exemple :

    ```cpp
    template class __declspec(dllexport) B<int>;
    class __declspec(dllexport) D : public B<int> {
    // ...
    ```

   Cette solution de contournement échoue si l’argument template est la classe dérivée. Par exemple :

    ```cpp
    class __declspec(dllexport) D : public B<D> {
    // ...
    ```

   Étant donné qu’il s’agit d’un modèle commun avec les modèles, le compilateur a modifié la sémantique de **dllexport** lorsqu’il est appliqué à une classe qui a une ou plusieurs classes de base et lorsqu’une ou plusieurs des classes de base sont une spécialisation d’un modèle de classe. Dans ce cas, le compilateur applique implicitement **dllexport** aux spécialisations des modèles de classe. Vous pouvez effectuer les opérations suivantes et ne pas recevoir d’avertissement :

    ```cpp
    class __declspec(dllexport) D : public B<D> {
    // ...
    ```

**Fin de la section spécifique de Microsoft**

## <a name="see-also"></a>Voir aussi

[dllexport, dllimport](../cpp/dllexport-dllimport.md)