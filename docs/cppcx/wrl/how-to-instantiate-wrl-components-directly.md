---
title: 'Comment : instancier directement les composants WRL'
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 1a9fa011-0cee-4abf-bf83-49adf53ff906
ms.openlocfilehash: f291e982d7f77c63821e5943a5867662ccd1b4fa
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213900"
---
# <a name="how-to-instantiate-wrl-components-directly"></a>Comment : instancier directement les composants WRL

Découvrez comment utiliser les fonctions Windows Runtime C++ Template Library (WRL)[Microsoft :: WRL :: Make](make-function.md) et [microsoft :: WRL ::D étails :: MakeAndInitialize](makeandinitialize-function.md) pour instancier un composant à partir du module qui le définit.

En instanciant les composants directement, vous pouvez réduire la charge lorsque vous n’avez pas besoin de fabriques de classes ou d’autres mécanismes. Vous pouvez instancier un composant directement dans les applications plateforme Windows universelle et dans les applications de bureau.

Pour savoir comment utiliser Windows Runtime C++ bibliothèque de modèles pour créer un composant com classique et l’instancier à partir d’une application de bureau externe, consultez [procédure : créer un composant com classique](how-to-create-a-classic-com-component-using-wrl.md).

Ce document présente deux exemples. Le premier exemple utilise la fonction `Make` pour instancier un composant. Le deuxième exemple utilise la fonction `MakeAndInitialize` pour instancier un composant qui peut échouer pendant la construction. (Étant donné que COM utilise généralement des valeurs HRESULT, plutôt que des exceptions, pour indiquer des erreurs, un type COM ne lève généralement pas à partir de son constructeur. `MakeAndInitialize` permet à un composant de valider ses arguments de construction via la méthode `RuntimeClassInitialize`.) Les deux exemples définissent une interface de journal de base et implémentent cette interface en définissant une classe qui écrit des messages dans la console.

> [!IMPORTANT]
> Vous ne pouvez pas utiliser l’opérateur `new` pour C++ instancier des composants de bibliothèque de modèles Windows Runtime. Par conséquent, nous vous recommandons de toujours utiliser `Make` ou `MakeAndInitialize` pour instancier un composant directement.

### <a name="to-create-and-instantiate-a-basic-logger-component"></a>Pour créer et instancier un composant d’enregistreur d’événements de base

1. Dans Visual Studio, créez un projet d' **application console Win32** . Nommez le projet, par exemple, *WRLLogger*.

2. Ajoutez un fichier **MIDL (. idl)** au projet, nommez le fichier `ILogger.idl`, puis ajoutez le code suivant :

   [!code-cpp[wrl-logger-make#1](../codesnippet/CPP/how-to-instantiate-wrl-components-directly_1.idl)]

3. Utilisez le code suivant pour remplacer le contenu de `WRLLogger.cpp`.

   [!code-cpp[wrl-logger-make#2](../codesnippet/CPP/how-to-instantiate-wrl-components-directly_2.cpp)]

### <a name="to-handle-construction-failure-for-the-basic-logger-component"></a>Pour gérer l’échec de construction du composant de l’enregistreur de journal de base

1. Utilisez le code suivant pour remplacer la définition de la classe `CConsoleWriter`. Cette version contient une variable membre de chaîne privée et substitue la méthode `RuntimeClass::RuntimeClassInitialize`. `RuntimeClassInitialize` échoue en cas d’échec de l’appel à `SHStrDup`.

   [!code-cpp[wrl-logger-makeandinitialize#1](../codesnippet/CPP/how-to-instantiate-wrl-components-directly_3.cpp)]

2. Utilisez le code suivant pour remplacer la définition de `wmain`. Cette version utilise `MakeAndInitialize` pour instancier l’objet `CConsoleWriter` et vérifie le résultat HRESULT.

   [!code-cpp[wrl-logger-makeandinitialize#2](../codesnippet/CPP/how-to-instantiate-wrl-components-directly_4.cpp)]

## <a name="see-also"></a>Voir aussi

[Bibliothèque de modèles Windows Runtime C++ (WRL)](windows-runtime-cpp-template-library-wrl.md)<br/>
[Microsoft :: WRL :: Make](make-function.md)<br/>
[Microsoft :: WRL ::D étails :: MakeAndInitialize](makeandinitialize-function.md)
