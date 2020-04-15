---
title: Classes de politique de copie ATL
ms.date: 11/04/2016
helpviewer_keywords:
- data [C++], ATL
- classes [C++], copy policy
- copy policy classes [C++]
- _Copy class
- _CopyInterface class
ms.assetid: 06704b68-d318-4c5d-a65b-71457fe9d00d
ms.openlocfilehash: f40f31124d4547076249a7459ac4b63cc25305d1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81317383"
---
# <a name="atl-copy-policy-classes"></a>Classes de politique de copie ATL

Les catégories de polices de copie sont [des classes d’utilité](../atl/utility-classes.md) utilisées pour initialiser, copier et supprimer des données. Les classes de police de copie vous permettent de définir la sémantique de copie pour n’importe quel type de données, et de définir les conversions entre les différents types de données.

ATL utilise des classes de police de copie dans ses implémentations des modèles suivants :

- [CComEnumImpl](../atl/reference/ccomenumimpl-class.md)

- [IEnumOnSTLImpl](../atl/reference/ienumonstlimpl-class.md)

- [ICollectionOnSTLImpl](../atl/reference/icollectiononstlimpl-class.md)

En encapsulant les informations nécessaires pour copier ou convertir des données dans une classe de police de copie qui peut être adoptée comme argument de modèle, les développeurs ATL ont prévu une réutilisabilité extrême de ces classes. Par exemple, si vous avez besoin de mettre en œuvre une collection à l’aide de n’importe quel type de données arbitraires, tout ce que vous devez fournir est la stratégie de copie appropriée; vous n’avez jamais à toucher le code qui implémente la collection.

## <a name="definition"></a>Définition

Par définition, une classe qui fournit les fonctions statiques suivantes est une classe de police de copie :

`static void init(` `DestinationType` `* p);`

`static HRESULT copy(` `DestinationType` `* pTo, const`  `SourceType` `* pFrom);`

`static void destroy(` `DestinationType` `* p);`

Vous pouvez remplacer `DestinationType` les types et *SourceType* par des types de données arbitraires pour chaque stratégie de copie.

> [!NOTE]
> Bien que vous puissiez définir des classes de police de copie pour tous les types de données arbitraires, l’utilisation des classes dans le code ATL devrait limiter les types qui ont du sens. Par exemple, lorsque vous utilisez une classe de stratégie de copie `DestinationType` avec les implémentations de collection ou d’enumérateur d’ATL, doit être un type qui peut être utilisé comme paramètre dans une méthode d’interface COM.

Utilisez **init** pour initialiser les données, **copier** pour copier des données et **détruire** pour libérer les données. Le sens précis de l’initialisation, de la copie et de la destruction est le domaine de la classe de la politique de copie et variera en fonction des types de données impliqués.

Il y a deux exigences en matière d’utilisation et de mise en œuvre d’une classe de police de copie :

- Le premier paramètre à **copier** ne doit recevoir qu’un pointeur sur les données que vous avez précédemment paralysées à l’aide **d’init**.

- **détruire** ne doit jamais recevoir un pointeur sur les données que vous avez déjà paralysé à l’aide **d’init** ou copié par **copie**.

## <a name="standard-implementations"></a>Mises en œuvre standard

ATL fournit deux classes de police `_Copy` `_CopyInterface` de copie sous la forme des classes et des modèles :

- La `_Copy` classe permet la copie homogène seulement (pas la conversion entre les types `DestinationType` de données) car il n’offre qu’un seul paramètre de modèle pour spécifier à la fois et *SourceType*. La mise en œuvre générique de ce `memcpy` modèle ne contient aucun code d’initialisation ou de destruction et utilise pour copier les données. ATL fournit également des `_Copy` spécialisations pour les types de données VARIANT, LPOLESTR, OLEVERB et CONNECTDATA.

- La `_CopyInterface` classe fournit une implémentation pour copier les pointeurs d’interface suivant les règles STANDARD com. Une fois de plus, cette classe ne permet que la `AddRef` copie homogène, de sorte qu’il utilise une affectation simple et un appel pour effectuer la copie.

## <a name="custom-implementations"></a>Implémentations personnalisées

En règle générale, vous devrez définir vos propres classes de police de copie pour la copie hétérogène (c’est-à-dire la conversion entre les types de données). Pour quelques exemples de classes de police de copie personnalisée, regardez les fichiers VCUE_Copy.h et VCUE_CopyString.h dans l’échantillon [ATLCollections.](../overview/visual-cpp-samples.md) Ces fichiers contiennent deux classes `GenericCopy` `MapCopy`de stratégie de copie de `GenericCopy` modèle, et , plus un certain nombre de spécialisations pour différents types de données.

### <a name="genericcopy"></a>GenericCopy GenericCopy

`GenericCopy`vous permet de spécifier le *SourceType* et `DestinationType` comme arguments de modèle. Voici la forme la plus `GenericCopy` générale de la classe de VCUE_Copy.h:

[!code-cpp[NVC_ATL_COM#30](../atl/codesnippet/cpp/atl-copy-policy-classes_1.h)]

VCUE_Copy.h contient également les spécialisations suivantes de `GenericCopy<BSTR>` `GenericCopy<VARIANT, BSTR>`cette `GenericCopy<BSTR, VARIANT>`classe: , . . VCUE_CopyString.h contient des spécialisations pour la copie de **std::string**s: `GenericCopy<std::string>`, `GenericCopy<VARIANT, std::string>`, et `GenericCopy<BSTR, std::string>`. Vous pourriez `GenericCopy` améliorer en fournissant d’autres spécialisations de votre propre.

### <a name="mapcopy"></a>MapCopy (en)

`MapCopy`suppose que les données copiées sont stockées dans une carte de style Bibliothèque standard, de sorte qu’elles vous permettent de spécifier le type de carte dans lequel les données sont stockées et le type de destination. La mise en œuvre de la classe utilise simplement les types fournis par la classe `GenericCopy` *MapType* pour déterminer le type de données source et appeler la classe appropriée. Aucune spécialisation de cette classe n’est nécessaire.

[!code-cpp[NVC_ATL_COM#31](../atl/codesnippet/cpp/atl-copy-policy-classes_2.h)]

## <a name="see-also"></a>Voir aussi

[Mise en œuvre d’une collection basée sur la bibliothèque standard de la C](../atl/implementing-an-stl-based-collection.md)<br/>
[Échantillon d’ATLCollections](../overview/visual-cpp-samples.md)
