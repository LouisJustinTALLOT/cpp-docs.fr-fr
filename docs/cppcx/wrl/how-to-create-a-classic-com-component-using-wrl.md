---
title: "Comment : créer un composant COM classique à l'aide de WRL"
description: Utilisez le Windows Runtime C++ Template Library (WRL) pour créer des composants COM classiques de base à utiliser dans les applications de bureau.
ms.date: 10/23/2020
ms.topic: reference
ms.openlocfilehash: 417c2e4635b380717662fa0762062f0228659de4
ms.sourcegitcommit: bf54b407169900bb668c85a67b31dbc0f069fe65
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2020
ms.locfileid: "92497192"
---
# <a name="how-to-create-a-classic-com-component-using-wrl"></a>Comment : créer un composant COM classique à l'aide de WRL

Vous pouvez utiliser le Windows Runtime C++ Template Library (WRL) pour créer des composants COM classiques de base à utiliser dans les applications de bureau, en plus de l’utiliser pour les applications plateforme Windows universelle (UWP). Pour la création de composants COM, la bibliothèque de modèles C++ Windows Runtime peut nécessiter moins de code que la bibliothèque ATL. Pour plus d’informations sur le sous-ensemble de COM pris en charge par la bibliothèque de modèles C++ Windows Runtime, consultez [Windows Runtime bibliothèque de modèles c++ (WRL)](windows-runtime-cpp-template-library-wrl.md).

Ce document montre comment utiliser la bibliothèque de modèles Windows Runtime C++ pour créer un composant COM de base. Bien que vous puissiez utiliser le mécanisme de déploiement qui correspond le mieux à vos besoins, ce document contient également une méthode de base pour inscrire et utiliser le composant COM à partir d'une application de bureau.

### <a name="to-use-the-windows-runtime-c-template-library-to-create-a-basic-classic-com-component"></a>Pour utiliser la bibliothèque de modèles C++ Windows Runtime pour créer un composant COM classique de base

1. Dans Visual Studio, créez un projet de **solution vide** . Nommez le projet, par exemple, `WRLClassicCOM` .

2. Ajoutez un **projet Win32** à la solution. Nommez le projet, par exemple, `CalculatorComponent` . Dans l’onglet Paramètres de l' **application** , sélectionnez **dll**.

3. Ajoutez un fichier **MIDL (. idl)** au projet. Nommez le fichier, par exemple, `CalculatorComponent.idl` .

4. Ajoutez ce code à CalculatorComponent.idl :

   [!code-cpp[wrl-classic-com-component#1](../codesnippet/CPP/how-to-create-a-classic-com-component-using-wrl_1.idl)]

5. Dans CalculatorComponent.cpp, définissez la classe `CalculatorComponent`. La `CalculatorComponent` classe hérite de [Microsoft :: WRL :: RuntimeClass](runtimeclass-class.md). [Microsoft :: WRL :: RuntimeClassFlags \<ClassicCom> ](runtimeclassflags-structure.md) Spécifie que la classe dérive de [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) et non de [IInspectable](/windows/win32/api/inspectable/nn-inspectable-iinspectable). ( `IInspectable` disponible uniquement pour Windows Runtime composants de l’application.) `CoCreatableClass` crée une fabrique pour la classe qui peut être utilisée avec des fonctions telles que [CoCreateInstance](/windows/win32/api/combaseapi/nf-combaseapi-cocreateinstance).

   [!code-cpp[wrl-classic-com-component#2](../codesnippet/CPP/how-to-create-a-classic-com-component-using-wrl_2.cpp)]

6. Utilisez le code suivant pour remplacer le code dans `dllmain.cpp` . Ce fichier définit les fonctions d'exportation DLL. Ces fonctions utilisent la classe [Microsoft :: WRL :: module](module-class.md) pour gérer les fabriques de classes pour le module.

   [!code-cpp[wrl-classic-com-component#3](../codesnippet/CPP/how-to-create-a-classic-com-component-using-wrl_3.cpp)]

7. Ajoutez un fichier de **définition de module (. def)** au projet. Nommez le fichier, par exemple, `CalculatorComponent.def` . Ce fichier fournit à l'éditeur de liens les noms des fonctions à exporter. Ouvrez la boîte de dialogue **pages de propriétés** de votre projet, puis sous **Propriétés de configuration**  >  entrée de l'**éditeur de liens**  >  **Input**, définissez la propriété fichier de **définition de module** sur votre fichier def.

8. Ajoutez ce code à CalculatorComponent.def :

    ```
    LIBRARY

    EXPORTS
        DllGetActivationFactory PRIVATE
        DllGetClassObject       PRIVATE
        DllCanUnloadNow         PRIVATE
    ```

9. Ajoutez runtimeobject.lib à la ligne de l'éditeur de liens. Pour en savoir plus, consultez [ `.Lib` fichiers en tant qu’entrée dans l’éditeur de liens](../../build/reference/dot-lib-files-as-linker-input.md).

### <a name="to-consume-the-com-component-from-a-desktop-app"></a>Pour utiliser le composant COM à partir d'une application de bureau

1. Inscrivez le composant COM dans le Registre Windows. Pour ce faire, créez un fichier des entrées d’inscription, nommez- `RegScript.reg` le, puis ajoutez le texte suivant. Remplacez *\<dll-path>* par le chemin d’accès de votre dll, par exemple `C:\temp\WRLClassicCOM\Debug\CalculatorComponent.dll` .

    ```
    Windows Registry Editor Version 5.00

    [HKEY_CLASSES_ROOT\Wow6432Node\CLSID\{E68F5EDD-6257-4E72-A10B-4067ED8E85F2}]
    @="CalculatorComponent Class"

    [HKEY_CLASSES_ROOT\Wow6432Node\CLSID\{E68F5EDD-6257-4E72-A10B-4067ED8E85F2}\InprocServer32]
    @="<dll-path>"
    "ThreadingModel"="Apartment"

    [HKEY_CLASSES_ROOT\Wow6432Node\CLSID\{E68F5EDD-6257-4E72-A10B-4067ED8E85F2}\Programmable]

    [HKEY_CLASSES_ROOT\Wow6432Node\CLSID\{E68F5EDD-6257-4E72-A10B-4067ED8E85F2}\TypeLib]
    @="{9D3E6826-CB8E-4D86-8B14-89F0D7EFCD01}"

    [HKEY_CLASSES_ROOT\Wow6432Node\CLSID\{E68F5EDD-6257-4E72-A10B-4067ED8E85F2}\Version]
    @="1.0"
    ```

2. Exécutez RegScript. reg ou ajoutez-le à l' **événement après génération**de votre projet. Pour plus d’informations, consultez boîte de [dialogue ligne de commande de l’événement pré-build/après génération](/visualstudio/ide/reference/pre-build-event-post-build-event-command-line-dialog-box).

3. Ajoutez un projet d' **application console Win32** à la solution. Nommez le projet, par exemple, `Calculator` .

4. Utilisez ce code pour remplacer le contenu de `Calculator.cpp` :

   [!code-cpp[wrl-classic-com-component#6](../codesnippet/CPP/how-to-create-a-classic-com-component-using-wrl_6.cpp)]

## <a name="robust-programming"></a>Programmation fiable

Ce document utilise des fonctions COM standard pour démontrer que vous pouvez utiliser la bibliothèque de modèles Windows Runtime C++ pour créer un composant COM et le rendre disponible pour n’importe quelle technologie COM. Vous pouvez également utiliser des types de bibliothèque de modèles Windows Runtime C++ tels que [Microsoft :: WRL :: ComPtr](comptr-class.md) dans votre application de bureau pour gérer la durée de vie de com et d’autres objets. Le code suivant utilise la bibliothèque de modèles Windows Runtime C++ pour gérer la durée de vie du `ICalculatorComponent` pointeur. La classe `CoInitializeWrapper` est un wrapper RAII qui garantit que la bibliothèque COM est libérée et également que la durée de vie de la bibliothèque COM est supérieure à celle de l'objet pointeur intelligent de `ComPtr`.

[!code-cpp[wrl-classic-com-component#7](../codesnippet/CPP/how-to-create-a-classic-com-component-using-wrl_7.cpp)]

## <a name="see-also"></a>Voir aussi

[Bibliothèque de modèles Windows Runtime C++ (WRL)](windows-runtime-cpp-template-library-wrl.md)
