---
description: 'En savoir plus sur : classes de stratégie de copie ATL'
title: Classes de stratégie de copie ATL
ms.date: 11/04/2016
helpviewer_keywords:
- data [C++], ATL
- classes [C++], copy policy
- copy policy classes [C++]
- _Copy class
- _CopyInterface class
ms.assetid: 06704b68-d318-4c5d-a65b-71457fe9d00d
ms.openlocfilehash: 502befadbd9317602c49d9a5815dee6ebc239d78
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97165756"
---
# <a name="atl-copy-policy-classes"></a>Classes de stratégie de copie ATL

Les classes de stratégie de copie sont des [classes utilitaires](../atl/utility-classes.md) utilisées pour initialiser, copier et supprimer des données. Les classes de stratégie de copie vous permettent de définir la sémantique de copie pour tout type de données et de définir des conversions entre différents types de données.

ATL utilise des classes de stratégie de copie dans ses implémentations des modèles suivants :

- [CComEnumImpl](../atl/reference/ccomenumimpl-class.md)

- [IEnumOnSTLImpl](../atl/reference/ienumonstlimpl-class.md)

- [ICollectionOnSTLImpl](../atl/reference/icollectiononstlimpl-class.md)

En encapsulant les informations nécessaires à la copie ou à la conversion des données dans une classe de stratégie de copie qui peut être passée comme argument template, les développeurs ATL ont fourni une réutilisabilité extrême de ces classes. Par exemple, si vous avez besoin d’implémenter une collection à l’aide d’un type de données arbitraire, il vous suffit de fournir la stratégie de copie appropriée ; vous n’avez jamais à toucher au code qui implémente la collection.

## <a name="definition"></a>Définition

Par définition, une classe qui fournit les fonctions statiques suivantes est une classe de stratégie de copie :

`static void init(` `DestinationType` `* p);`

`static HRESULT copy(` `DestinationType` `* pTo, const`  `SourceType` `* pFrom);`

`static void destroy(` `DestinationType` `* p);`

Vous pouvez remplacer les types `DestinationType` et *SourceType* par des types de données arbitraires pour chaque stratégie de copie.

> [!NOTE]
> Bien que vous puissiez définir des classes de stratégie de copie pour tous les types de données arbitraires, l’utilisation des classes dans le code ATL doit limiter les types qui ont un sens. Par exemple, lors de l’utilisation d’une classe de stratégie de copie avec des implémentations de collection ou d’énumérateur ATL, `DestinationType` doit être un type qui peut être utilisé comme paramètre dans une méthode d’interface com.

Utilisez **init** pour initialiser les données, **Copiez** -les pour copier les données, puis **détruisez** pour libérer les données. La signification précise de l’initialisation, de la copie et de la destruction est le domaine de la classe de stratégie de copie et varie selon les types de données impliqués.

Deux conditions sont requises pour l’utilisation et l’implémentation d’une classe de stratégie de copie :

- Le premier paramètre à **copier** doit uniquement recevoir un pointeur vers des données que vous avez précédemment initialisées à l’aide de **init**.

- **Destroy** ne doit jamais recevoir un pointeur vers des données que vous avez précédemment initialisées à l’aide d' **init** ou copiées via la **copie**.

## <a name="standard-implementations"></a>Implémentations standard

ATL fournit deux classes de stratégie de copie sous la forme `_Copy` des `_CopyInterface` classes de modèle et :

- La `_Copy` classe autorise uniquement la copie homogène (pas la conversion entre les types de données), car elle n’offre qu’un seul paramètre de modèle pour spécifier à la fois `DestinationType` et *SourceType*. L’implémentation générique de ce modèle ne contient pas de code d’initialisation ou de destruction et utilise `memcpy` pour copier les données. ATL fournit également des spécialisations de `_Copy` pour les types de données Variant, LPOLESTR, OLEVERB et CONNECTDATA.

- La `_CopyInterface` classe fournit une implémentation pour copier les pointeurs d’interface suivant les règles com standard. Une fois encore, cette classe autorise uniquement la copie homogène, donc elle utilise une assignation simple et un appel à `AddRef` pour effectuer la copie.

## <a name="custom-implementations"></a>Implémentations personnalisées

En règle générale, vous devez définir vos propres classes de stratégie de copie pour la copie hétérogène (c’est-à-dire la conversion entre les types de données). Pour obtenir des exemples de classes de stratégie de copie personnalisées, examinez les fichiers VCUE_Copy. h et VCUE_CopyString. h dans l’exemple [ATLCollections](../overview/visual-cpp-samples.md) . Ces fichiers contiennent deux classes de stratégie de copie `GenericCopy` de modèle, et `MapCopy` plus un certain nombre de spécialisations de `GenericCopy` pour différents types de données.

### <a name="genericcopy"></a>GenericCopy

`GenericCopy` vous permet de spécifier les paramètres *SourceType* et `DestinationType` comme arguments template. Voici la forme la plus générale de la `GenericCopy` classe à partir de VCUE_Copy. h :

[!code-cpp[NVC_ATL_COM#30](../atl/codesnippet/cpp/atl-copy-policy-classes_1.h)]

VCUE_Copy. h contient également les spécialisations suivantes de cette classe : `GenericCopy<BSTR>` , `GenericCopy<VARIANT, BSTR>` , `GenericCopy<BSTR, VARIANT>` . VCUE_CopyString. h contient des spécialisations pour la copie à partir de **std :: String** s : `GenericCopy<std::string>` , `GenericCopy<VARIANT, std::string>` et `GenericCopy<BSTR, std::string>` . Vous pouvez améliorer `GenericCopy` en fournissant vos propres spécialisations.

### <a name="mapcopy"></a>MapCopy

`MapCopy` Supposons que les données copiées sont stockées dans une table de style bibliothèque standard C++, ce qui vous permet de spécifier le type de mappage dans lequel les données sont stockées et le type de destination. L’implémentation de la classe utilise simplement les typedefs fournis par la classe *maptype* pour déterminer le type des données sources et appeler la `GenericCopy` classe appropriée. Aucune spécialisation de cette classe n’est nécessaire.

[!code-cpp[NVC_ATL_COM#31](../atl/codesnippet/cpp/atl-copy-policy-classes_2.h)]

## <a name="see-also"></a>Voir aussi

[Implémentation d’une collection Library-Based standard C++](../atl/implementing-an-stl-based-collection.md)<br/>
[Exemple ATLCollections](../overview/visual-cpp-samples.md)
