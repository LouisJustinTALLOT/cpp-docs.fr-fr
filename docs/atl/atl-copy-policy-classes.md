---
title: Classes de stratégies de copie ATL | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- data [C++], ATL
- classes [C++], copy policy
- copy policy classes [C++]
- _Copy class
- _CopyInterface class
ms.assetid: 06704b68-d318-4c5d-a65b-71457fe9d00d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 34b9ed5dca45633a5ab980d38b8a7cda151f5dc7
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32358525"
---
# <a name="atl-copy-policy-classes"></a>Classes de stratégies de copie ATL
Classes de stratégies de copie sont [classes utilitaires](../atl/utility-classes.md) utilisée pour initialiser, copier et supprimer des données. Elles permettent de définir une sémantique de copie pour n’importe quel type de données, et de définir des conversions entre différents types de données.  
  
 Classes de stratégies de copie utilise ATL dans ses implémentations des modèles suivants :  
  
-   [CComEnumImpl](../atl/reference/ccomenumimpl-class.md)  
  
-   [IEnumOnSTLImpl](../atl/reference/ienumonstlimpl-class.md)  
  
-   [ICollectionOnSTLImpl](../atl/reference/icollectiononstlimpl-class.md)  
  
 En encapsulant les informations nécessaires pour copier ou de convertir les données dans une classe de stratégie de copie qui peut être passée comme argument de modèle, les développeurs d’ATL ont fourni pour réutilisation extrêmes de ces classes. Par exemple, si vous avez besoin d’implémenter une collection à l’aide de n’importe quel type de données arbitraires, il vous suffit de fournir est la stratégie de copie appropriée ; Vous devrez jamais toucher au code qui implémente la collection.  
  
## <a name="definition"></a>Définition  
 Par définition, une classe qui fournit les fonctions statiques suivantes est une classe de stratégies de copie :  
  
 `static void init(` `DestinationType` `* p);`  
  
 `static HRESULT copy(` `DestinationType` `* pTo, const`  `SourceType` `* pFrom);`  
  
 `static void destroy(` `DestinationType` `* p);`  
  
 Vous pouvez remplacer les types `DestinationType` et *SourceType* avec les types de données arbitraires pour chaque copie de la stratégie.  
  
> [!NOTE]
>  Bien que vous pouvez définir des classes de stratégies de copie pour les types de données arbitraires, utilisation des classes dans le code ATL doit limiter les types qui ont un sens. Par exemple, quand une copie de la stratégie à l’aide de la classe avec des collections d’ATL ou des implémentations de l’énumérateur, `DestinationType` doit être un type qui peut être utilisé en tant que paramètre dans une méthode d’interface COM.  
  
 Utilisez **init** pour initialiser les données, **copie** pour copier les données, et **détruire** pour libérer les données. La signification précise de l’initialisation, la copie et la destruction sont dans le domaine de la classe de stratégie de copie et varient en fonction des types de données impliqués.  
  
 Il existe deux exigences sur l’utilisation et l’implémentation d’une classe de stratégie de copie :  
  
-   Le premier paramètre de **copie** doivent recevoir uniquement un pointeur vers les données que vous avez précédemment initialisé à l’aide de **init**.  
  
-   **détruire** doivent recevoir uniquement un pointeur vers les données que vous avez précédemment initialisé à l’aide de **init** ou copiés via **copie**.  
  
## <a name="standard-implementations"></a>Implémentations standard  
 ATL fournit deux classes de stratégie de copie sous la forme de la **_Copy** et **_CopyInterface** classes de modèle :  
  
-   Le **_Copy** classe ne permet que la copie homogène (pas la conversion entre types de données), car elle offre uniquement un paramètre de modèle unique pour spécifier les deux `DestinationType` et *SourceType*. L’implémentation générique de ce modèle ne contient aucun code d’initialisation ou de destruction et utilise `memcpy` pour copier les données. ATL fournit également des spécialisations de **_Copy** pour **VARIANT**, `LPOLESTR`, **OLEVERB**, et **CONNECTDATA** des types de données.  
  
-   Le **_CopyInterface** classe fournit une implémentation pour la copie des pointeurs d’interface suivant les règles COM standard. Une fois encore cette classe permet de seulement copie homogène, afin qu’il utilise une assignation simple et un appel à `AddRef` pour effectuer la copie.  
  
## <a name="custom-implementations"></a>Implémentations personnalisées  
 En règle générale, vous devez définir vos propres classes de stratégie de copie pour la copie hétérogène (autrement dit, la conversion entre types de données). Pour obtenir des exemples de classes de stratégie de copie personnalisée, examinez les fichiers VCUE_Copy.h et VCUE_CopyString.h dans le [ATLCollections](../visual-cpp-samples.md) exemple. Ces fichiers contiennent deux classes de stratégie de copie de modèle, `GenericCopy` et `MapCopy`, ainsi que plusieurs spécialisations de `GenericCopy` pour différents types de données.  
  
### <a name="genericcopy"></a>GenericCopy  
 `GenericCopy` Vous pouvez spécifier le *SourceType* et `DestinationType` en tant qu’arguments de modèle. Voici la forme la plus générale de la `GenericCopy` classe VCUE_Copy.h :  
  
 [!code-cpp[NVC_ATL_COM#30](../atl/codesnippet/cpp/atl-copy-policy-classes_1.h)]  
  
 VCUE_Copy.h contient également les spécialisations suivantes de cette classe : `GenericCopy<BSTR>`, `GenericCopy<VARIANT, BSTR>`, `GenericCopy<BSTR, VARIANT>`. VCUE_CopyString.h contient les spécialisations de la copie de **std::string**s: `GenericCopy<std::string>`, `GenericCopy<VARIANT, std::string>`, et `GenericCopy<BSTR, std::string>`. Vous pouvez améliorer `GenericCopy` en fournissant vos propres spécialisations.  
  
### <a name="mapcopy"></a>MapCopy  
 `MapCopy` suppose que les données copiées sont stockées dans un mappage de type de bibliothèque C++ Standard, donc il permet de spécifier le type de carte dans laquelle les données sont stockées et le type de destination. L’implémentation de la classe utilise seulement les typedefs fournis par le *MapType* classe pour déterminer le type de la source de données et appeler approprié `GenericCopy` classe. Aucune des spécialisations de cette classe ne sont nécessaires.  
  
 [!code-cpp[NVC_ATL_COM#31](../atl/codesnippet/cpp/atl-copy-policy-classes_2.h)]  
  
## <a name="see-also"></a>Voir aussi  
 [Implémentation d’un regroupement de bibliothèque C++ Standard](../atl/implementing-an-stl-based-collection.md)   
 [ATLCollections, exemple](../visual-cpp-samples.md)

