---
title: 'Procédure : Créer un composant COM classique à l’aide de WRL'
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 5efe7690-90d5-4c3c-9e53-11a14cefcb19
ms.openlocfilehash: bb38f36cdd481e61d049f82159fdc24c3726f646
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62398327"
---
# <a name="how-to-create-a-classic-com-component-using-wrl"></a>Procédure : Créer un composant COM classique à l’aide de WRL

Vous pouvez utiliser la bibliothèque de modèles C++ (WRL) de Windows Runtime pour créer des composants COM classiques base pour une utilisation dans des applications de bureau, outre l’utilisation pour les applications de plateforme universelle Windows (UWP). Pour la création de composants COM, la bibliothèque de modèles Windows Runtime C++ peut nécessiter moins de code que l’ATL. Pour plus d’informations sur le sous-ensemble de COM qui prend en charge de la bibliothèque de modèles Windows Runtime C++, consultez [bibliothèque de modèles Windows Runtime C++ (WRL)](windows-runtime-cpp-template-library-wrl.md).

Ce document montre comment utiliser la bibliothèque de modèles Windows Runtime C++ pour créer un composant COM de base. Bien que vous puissiez utiliser le mécanisme de déploiement qui correspond le mieux à vos besoins, ce document contient également une méthode de base pour inscrire et utiliser le composant COM à partir d'une application de bureau.

### <a name="to-use-the-windows-runtime-c-template-library-to-create-a-basic-classic-com-component"></a>Pour utiliser la bibliothèque de modèles Windows Runtime C++ pour créer un composant COM classique de base

1. Dans Visual Studio, créez un **nouvelle Solution** projet. Nommez le projet, par exemple, `WRLClassicCOM`.

2. Ajouter un **projet Win32** à la solution. Nommez le projet, par exemple, `CalculatorComponent`. Sur le **paramètres d’Application** onglet, sélectionnez **DLL**.

3. Ajouter un **fichier Midl (.idl)** fichier au projet. Nommez le fichier, par exemple, `CalculatorComponent.idl`.

4. Ajoutez ce code à CalculatorComponent.idl :

   [!code-cpp[wrl-classic-com-component#1](../codesnippet/CPP/how-to-create-a-classic-com-component-using-wrl_1.idl)]

5. Dans CalculatorComponent.cpp, définissez la classe `CalculatorComponent`. Le `CalculatorComponent` hérite de la classe [Microsoft::wrl :: runtimeclass](runtimeclass-class.md). [Microsoft::wrl :: runtimeclassflags\<ClassicCom >](runtimeclassflags-structure.md) Spécifie que la classe dérive de [IUnknown](/windows/desktop/api/unknwn/nn-unknwn-iunknown) et non [IInspectable](/windows/desktop/api/inspectable/nn-inspectable-iinspectable). (`IInspectable` est disponible uniquement pour les composants d’application Windows Runtime.) `CoCreatableClass` crée une fabrique pour la classe qui peut être utilisée avec des fonctions telles que [CoCreateInstance](/windows/desktop/api/combaseapi/nf-combaseapi-cocreateinstance).

   [!code-cpp[wrl-classic-com-component#2](../codesnippet/CPP/how-to-create-a-classic-com-component-using-wrl_2.cpp)]

6. Utilisez le code suivant pour remplacer le code dans `dllmain.cpp`. Ce fichier définit les fonctions d'exportation DLL. Ces fonctions utilisent la [Microsoft::wrl :: module](module-class.md) classe pour gérer les fabriques de classe pour le module.

   [!code-cpp[wrl-classic-com-component#3](../codesnippet/CPP/how-to-create-a-classic-com-component-using-wrl_3.cpp)]

7. Ajouter un **le fichier de définition de Module (.def)** fichier au projet. Nommez le fichier, par exemple, `CalculatorComponent.def`. Ce fichier fournit à l'éditeur de liens les noms des fonctions à exporter.

8. Ajoutez ce code à CalculatorComponent.def :

    ```
    LIBRARY

    EXPORTS
        DllGetActivationFactory PRIVATE
        DllGetClassObject       PRIVATE
        DllCanUnloadNow         PRIVATE
    ```

9. Ajoutez runtimeobject.lib à la ligne de l'éditeur de liens. Pour savoir comment procéder, consultez [. Fichiers lib en tant qu’entrée de l’éditeur de liens](../../build/reference/dot-lib-files-as-linker-input.md).

### <a name="to-consume-the-com-component-from-a-desktop-app"></a>Pour utiliser le composant COM à partir d'une application de bureau

1. Inscrivez le composant COM dans le Registre Windows. Pour ce faire, créez un fichier d’entrées d’inscription, nommez-le `RegScript.reg`et ajoutez le texte suivant. Remplacez  *\<dll-path >* avec le chemin d’accès de votre DLL — par exemple, `C:\temp\WRLClassicCOM\Debug\CalculatorComponent.dll`.

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

2. Exécutez RegScript.reg ou ajoutez-le à votre projet **événement post-Build**. Pour plus d’informations, consultez [pré-build/Post-build ligne de commande boîte de dialogue événement](/visualstudio/ide/reference/pre-build-event-post-build-event-command-line-dialog-box).

3. Ajouter un **Application Console Win32** projet à la solution. Nommez le projet, par exemple, `Calculator`.

4. Utilisez ce code pour remplacer le contenu de `Calculator.cpp`:

   [!code-cpp[wrl-classic-com-component#6](../codesnippet/CPP/how-to-create-a-classic-com-component-using-wrl_6.cpp)]

## <a name="robust-programming"></a>Programmation fiable

Ce document utilise des fonctions COM standard pour montrer que vous pouvez utiliser la bibliothèque de modèles Windows Runtime C++ pour créer un composant COM et le rendre disponible à n’importe quelle technologie compatible COM. Vous pouvez également utiliser des types de bibliothèque de modèles C++ Windows Runtime tel que [Microsoft::wrl :: comptr](comptr-class.md) dans votre application de bureau pour gérer la durée de vie de COM et d’autres objets. Le code suivant utilise la bibliothèque de modèles C++ Windows Runtime pour gérer la durée de vie de la `ICalculatorComponent` pointeur. La classe `CoInitializeWrapper` est un wrapper RAII qui garantit que la bibliothèque COM est libérée et également que la durée de vie de la bibliothèque COM est supérieure à celle de l'objet pointeur intelligent de `ComPtr`.

[!code-cpp[wrl-classic-com-component#7](../codesnippet/CPP/how-to-create-a-classic-com-component-using-wrl_7.cpp)]

## <a name="see-also"></a>Voir aussi

[Bibliothèque de modèles Windows Runtime C++ (WRL)](windows-runtime-cpp-template-library-wrl.md)