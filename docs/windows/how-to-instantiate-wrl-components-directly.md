---
title: 'Comment : instancier directement les composants WRL'
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 1a9fa011-0cee-4abf-bf83-49adf53ff906
ms.openlocfilehash: 2da1bd65631d33f3e1edb67efb5e94f270f1f1ea
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50523186"
---
# <a name="how-to-instantiate-wrl-components-directly"></a>Comment : instancier directement les composants WRL

Découvrez comment utiliser la bibliothèque de modèles C++ (WRL) de Windows Runtime[Microsoft::wrl :: Make](../windows/make-function.md) et [Microsoft::WRL::Details::MakeAndInitialize](../windows/makeandinitialize-function.md) pour instancier un composant à partir du module qui Il définit.

En instanciant des composants directement, vous pouvez réduire la surcharge lorsque vous n’avez pas besoin des fabriques de classe ou d’autres mécanismes. Vous pouvez instancier un composant directement dans les deux applications de plateforme Windows universelle et dans les applications de bureau.

Pour savoir comment utiliser la bibliothèque de modèles Windows Runtime C++ pour créer un composant COM classique et l’instancier à partir d’une application de bureau externe, consultez [Comment : créer un composant COM classique](../windows/how-to-create-a-classic-com-component-using-wrl.md).

Ce document montre deux exemples. Le premier exemple utilise le `Make` fonction pour instancier un composant. Le deuxième exemple utilise le `MakeAndInitialize` fonction pour instancier un composant peut échouer lors de la construction. (Étant donné que COM utilise généralement des valeurs HRESULT, au lieu d’exceptions, pour indiquer des erreurs, un type COM en général, ne lève pas de son constructeur. `MakeAndInitialize` permet à un composant à valider ses arguments de construction via la `RuntimeClassInitialize` méthode.) Les deux exemples définissent une interface de journal de base et implémentent cette interface en définissant une classe qui écrit des messages dans la console.

> [!IMPORTANT]
> Vous ne pouvez pas utiliser le **nouveau** opérateur pour instancier les composants de la bibliothèque de modèles C++ Windows Runtime. Par conséquent, nous recommandons de toujours utiliser `Make` ou `MakeAndInitialize` pour instancier un composant directement.

### <a name="to-create-and-instantiate-a-basic-logger-component"></a>Pour créer et instancier un composant de journal de base

1. Dans Visual Studio, créez un **Application Console Win32** projet. Nommez le projet, par exemple, *WRLLogger*.

2. Ajouter un **fichier Midl (.idl)** fichier au projet, nommez le fichier `ILogger.idl`, puis ajoutez ce code :

   [!code-cpp[wrl-logger-make#1](../windows/codesnippet/CPP/how-to-instantiate-wrl-components-directly_1.idl)]

3. Utilisez le code suivant pour remplacer le contenu de `WRLLogger.cpp`.

   [!code-cpp[wrl-logger-make#2](../windows/codesnippet/CPP/how-to-instantiate-wrl-components-directly_2.cpp)]

### <a name="to-handle-construction-failure-for-the-basic-logger-component"></a>Pour gérer l’échec de construction pour le composant de journal de base

1. Utilisez le code suivant pour remplacer la définition de la `CConsoleWriter` classe. Cette version conserve un membre privé chaîne variable et substitue le `RuntimeClass::RuntimeClassInitialize` (méthode). `RuntimeClassInitialize` échoue si l’appel à `SHStrDup` échoue.

   [!code-cpp[wrl-logger-makeandinitialize#1](../windows/codesnippet/CPP/how-to-instantiate-wrl-components-directly_3.cpp)]

2. Utilisez le code suivant pour remplacer la définition de `wmain`. Cette version utilise `MakeAndInitialize` pour instancier le `CConsoleWriter` de l’objet et vérifie le résultat HRESULT.

   [!code-cpp[wrl-logger-makeandinitialize#2](../windows/codesnippet/CPP/how-to-instantiate-wrl-components-directly_4.cpp)]

## <a name="see-also"></a>Voir aussi

[Bibliothèque de modèles Windows Runtime C++ (WRL)](../windows/windows-runtime-cpp-template-library-wrl.md)<br/>
[Microsoft::wrl :: Make](../windows/make-function.md)<br/>
[Microsoft::wrl::Details::MakeAndInitialize](../windows/makeandinitialize-function.md)