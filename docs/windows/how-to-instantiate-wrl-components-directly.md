---
title: 'Comment : instancier directement les composants WRL | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
ms.assetid: 1a9fa011-0cee-4abf-bf83-49adf53ff906
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 127a8430e79e7963ea94646f70179df2f30450ff
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
---
# <a name="how-to-instantiate-wrl-components-directly"></a>Comment : instancier directement les composants WRL
Découvrez comment utiliser la bibliothèque de modèles C++ (WRL) de Windows Runtime[Microsoft::wrl :: Make](../windows/make-function.md) et [Microsoft::WRL::Details::MakeAndInitialize](../windows/makeandinitialize-function.md) pour instancier un composant à partir du module qui Il définit.  
  
 En instanciant directement les composants, vous pouvez réduire la surcharge lorsque vous n’avez pas besoin des fabriques de classe ou d’autres mécanismes. Vous pouvez instancier un composant directement dans les deux applications de plateforme Windows universelle et applications de bureau.  
  
Pour savoir comment utiliser la bibliothèque de modèles Windows Runtime C++ pour créer un composant COM classique et l’instancier à partir d’une application de bureau externe, consultez [Comment : créer un composant COM classique](../windows/how-to-create-a-classic-com-component-using-wrl.md).  
  
 Ce document montre deux exemples. Le premier exemple utilise la `Make` fonction pour instancier un composant. Le deuxième exemple utilise la `MakeAndInitialize` fonction pour instancier un composant peut échouer pendant la construction. (Étant donné que COM utilise généralement `HRESULT` valeurs, au lieu des exceptions, pour indiquer les erreurs, un type COM généralement ne lève pas à partir de son constructeur. `MakeAndInitialize` permet à un composant valider ses arguments de construction via la `RuntimeClassInitialize` méthode.) Les deux exemples, définissent une interface de journal de base et implémentent cette interface en définissant une classe qui écrit des messages dans la console.  
  
> [!IMPORTANT]
>  Vous ne pouvez pas utiliser le `new` opérateur pour instancier les composants de la bibliothèque de modèles Windows Runtime C++. Par conséquent, nous vous recommandons de toujours utiliser `Make` ou `MakeAndInitialize` pour instancier un composant directement.  
  
### <a name="to-create-and-instantiate-a-basic-logger-component"></a>Pour créer et instancier un composant de journal de base  
  
1.  Dans Visual Studio, créez un **Application Console Win32** projet. Nommez le projet, par exemple, `WRLLogger`.  
  
2.  Ajouter un **fichier Midl (.idl)** de fichiers au projet, nommez le fichier `ILogger.idl`, puis ajoutez ce code :  
  
     [!code-cpp[wrl-logger-make#1](../windows/codesnippet/CPP/how-to-instantiate-wrl-components-directly_1.idl)]  
  
3.  Utilisez le code suivant pour remplacer le contenu de WRLLogger.cpp.  
  
     [!code-cpp[wrl-logger-make#2](../windows/codesnippet/CPP/how-to-instantiate-wrl-components-directly_2.cpp)]  
  
### <a name="to-handle-construction-failure-for-the-basic-logger-component"></a>Pour gérer l’échec de construction pour le composant de journal de base  
  
1.  Utilisez le code suivant pour remplacer la définition de la `CConsoleWriter` classe. Cette version conserve un membre privé chaîne variable et substitue le `RuntimeClass::RuntimeClassInitialize` (méthode). `RuntimeClassInitialize` échoue si l’appel à `SHStrDup` échoue.  
  
     [!code-cpp[wrl-logger-makeandinitialize#1](../windows/codesnippet/CPP/how-to-instantiate-wrl-components-directly_3.cpp)]  
  
2.  Utilisez le code suivant pour remplacer la définition de `wmain`. Cette version utilise `MakeAndInitialize` pour instancier le `CConsoleWriter` objet et vérifie le `HRESULT` résultat.  
  
     [!code-cpp[wrl-logger-makeandinitialize#2](../windows/codesnippet/CPP/how-to-instantiate-wrl-components-directly_4.cpp)]  
  
## <a name="see-also"></a>Voir aussi  
 [Windows Runtime bibliothèque de modèles C++ (WRL)](../windows/windows-runtime-cpp-template-library-wrl.md)   
 [Microsoft::wrl :: Make](../windows/make-function.md)   
 [Microsoft::wrl::Details::MakeAndInitialize](../windows/makeandinitialize-function.md)