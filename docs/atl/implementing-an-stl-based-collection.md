---
title: Mise en œuvre d’une collection basée sur la bibliothèque standard de la C
ms.date: 11/04/2016
helpviewer_keywords:
- ICollectionOnSTLImpl interface
ms.assetid: 6d49f819-1957-4813-b074-3f12c494d8ca
ms.openlocfilehash: e80ce5e7bbc6b9c6be1615dad1ea43c18e03eb55
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319439"
---
# <a name="implementing-a-c-standard-library-based-collection"></a>Mise en œuvre d’une collection basée sur la bibliothèque standard de la C

ATL fournit `ICollectionOnSTLImpl` l’interface pour vous permettre d’implémenter rapidement des interfaces de collecte basées sur la bibliothèque standard de CMD sur vos objets. Pour comprendre le fonctionnement de cette classe, vous travaillerez à travers un exemple simple (ci-dessous) qui utilise cette classe pour implémenter une collection de lecture uniquement destinée aux clients Automation.

Le code de l’échantillon provient de [l’échantillon ATLCollections](../overview/visual-cpp-samples.md).

Pour compléter cette procédure, vous :

- [Générer un nouvel objet simple](#vccongenerating_an_object).

- [Modifier le fichier IDL](#vcconedit_the_idl) pour l’interface générée.

- [Créez cinq types décrivant](#vcconstorage_and_exposure_typedefs) comment les éléments de collecte sont stockés et comment ils seront exposés aux clients via les interfaces COM.

- [Créez deux types pour les classes de police de copie.](#vcconcopy_classes)

- [Créez des types pour l’enumérateur et les implémentations de collecte.](#vcconenumeration_and_collection)

- [Modifier le code CMD généré par l’assistant pour utiliser le type de collection](#vcconedit_the_generated_code).

- [Ajouter du code pour remplir la collection](#vcconpopulate_the_collection).

## <a name="generating-a-new-simple-object"></a><a name="vccongenerating_an_object"></a>Génération d’un nouvel objet simple

Créez un nouveau projet, en veillant à ce que la boîte Attributs sous paramètres d’application soit effacée. Utilisez la boîte de dialogue ATL Add Class et ajouter `Words`Simple Object Wizard pour générer un objet simple appelé . Assurez-vous qu’une `IWords` double interface appelée est générée. Les objets de la classe générée seront utilisés pour représenter une collection de mots (c’est-à-dire des cordes).

## <a name="editing-the-idl-file"></a><a name="vcconedit_the_idl"></a>Rédaction du fichier IDL

Maintenant, ouvrez le fichier IDL et `IWords` ajoutez les trois propriétés nécessaires pour se transformer en une interface de collecte de lecture uniquement, comme indiqué ci-dessous:

[!code-cpp[NVC_ATL_COM#24](../atl/codesnippet/cpp/implementing-an-stl-based-collection_1.idl)]

Il s’agit du formulaire standard pour une interface de collecte de lecture uniquement conçue avec les clients Automation à l’esprit. Les commentaires numérotés dans cette définition d’interface correspondent aux commentaires ci-dessous :

1. Les interfaces de collecte sont généralement `_NewEnum` doubles `IDispatch::Invoke`parce que les clients Automation accèdent à la propriété via . Cependant, les clients Automation peuvent accéder aux méthodes restantes via le vtable, de sorte que les interfaces doubles sont préférables à des dispinterfaces.

1. Si une double interface ou une dispinterface ne sera pas prolongée au moment de `IDispatch::Invoke`l’exécution (c’est-à-dire que vous ne fournirez pas de méthodes ou de propriétés supplémentaires via), vous devez appliquer l’attribut **inexistant** à votre définition. Cet attribut permet aux clients d’Automation d’effectuer une vérification complète du code au moment de la compilation. Dans ce cas, l’interface ne doit pas être étendue.

1. Le DISPID correct est important si vous voulez que les clients Automation soient en mesure d’utiliser cette propriété. (Notez qu’il n’y a qu’un seul souligne dans DISPID_NEWENUM.)

1. Vous pouvez fournir n’importe quelle `Item` valeur comme le DISPID de la propriété. Cependant, `Item` utilise généralement DISPID_VALUE pour en faire la propriété par défaut de la collection. Cela permet aux clients d’Automation de se référer à la propriété sans la nommer explicitement.

1. Le type de données utilisé `Item` pour la valeur de retour de la propriété est le type de l’article stocké dans la collection en ce qui concerne les clients COM. L’interface renvoie les chaînes, vous devriez donc utiliser le type de chaîne COM standard, BSTR. Vous pouvez stocker les données dans un format différent en interne comme vous le verrez sous peu.

1. La valeur utilisée pour le `Count` DISPID de la propriété est complètement arbitraire. Il n’y a pas de DISPID standard pour cette propriété.

## <a name="creating-typedefs-for-storage-and-exposure"></a><a name="vcconstorage_and_exposure_typedefs"></a>Création de types pour le stockage et l’exposition

Une fois l’interface de collecte définie, vous devez décider comment les données seront stockées et comment les données seront exposées via l’enumérateur.

Les réponses à ces questions peuvent être fournies sous la forme d’un certain nombre de types, que vous pouvez ajouter près du haut du fichier d’en-tête pour votre classe nouvellement créée:

[!code-cpp[NVC_ATL_COM#25](../atl/codesnippet/cpp/implementing-an-stl-based-collection_2.h)]

Dans ce cas, vous stockerez les données comme un **std::vector** de **std::string.** **std::vector** est une classe de conteneurs de bibliothèque standard de C qui se comporte comme un tableau géré. **std::string** est la classe de cordes de la bibliothèque standard de C. Ces classes facilitent le travail avec une collection de cordes.

Étant donné que le support Visual Basic est essentiel au succès `_NewEnum` de cette `IEnumVARIANT` interface, l’enumérateur retourné par la propriété doit prendre en charge l’interface. C’est la seule interface d’enumérateur comprise par Visual Basic.

## <a name="creating-typedefs-for-copy-policy-classes"></a><a name="vcconcopy_classes"></a>Création de types pour les classes de politiques de copie

Les types que vous avez créés jusqu’à présent fournissent toutes les informations dont vous avez besoin pour créer d’autres types pour les classes de copie qui seront utilisées par l’enumérateur et la collecte:

[!code-cpp[NVC_ATL_COM#26](../atl/codesnippet/cpp/implementing-an-stl-based-collection_3.h)]

Dans cet exemple, vous `GenericCopy` pouvez utiliser la classe personnalisée définie dans VCUE_Copy.h et VCUE_CopyString.h à partir de l’échantillon [ATLCollections.](../overview/visual-cpp-samples.md) Vous pouvez utiliser cette classe dans d’autres codes, mais `GenericCopy` vous devrez peut-être définir d’autres spécialisations pour prendre en charge les types de données utilisés dans vos propres collections. Pour plus d’informations, voir [ATL Copy Policy Classes](../atl/atl-copy-policy-classes.md).

## <a name="creating-typedefs-for-enumeration-and-collection"></a><a name="vcconenumeration_and_collection"></a>Création de types pour l’énumération et la collection

Maintenant, tous les paramètres de `CComEnumOnSTL` `ICollectionOnSTLImpl` modèle nécessaires pour se spécialiser dans les classes et les classes pour cette situation ont été fournis sous la forme de types. Pour simplifier l’utilisation des spécialisations, créez deux autres types comme indiqué ci-dessous :

[!code-cpp[NVC_ATL_COM#27](../atl/codesnippet/cpp/implementing-an-stl-based-collection_4.h)]

Maintenant `CollectionType` est un synonyme pour `ICollectionOnSTLImpl` une spécialisation `IWords` de qui implémente l’interface définie précédemment et fournit un enumérateur qui prend en charge `IEnumVARIANT`.

## <a name="editing-the-wizard-generated-code"></a><a name="vcconedit_the_generated_code"></a>Modification du code généré par wizard

Maintenant, vous `CWords` devez dériver de `CollectionType` la mise en `IWords`œuvre de l’interface représentée par le tapdef plutôt que , comme indiqué ci-dessous:

[!code-cpp[NVC_ATL_COM#28](../atl/codesnippet/cpp/implementing-an-stl-based-collection_5.h)]

## <a name="adding-code-to-populate-the-collection"></a><a name="vcconpopulate_the_collection"></a>Ajout de code pour peupler la collection

La seule chose qui reste est de remplir le vecteur avec des données. Dans cet exemple simple, vous pouvez ajouter quelques mots à la collection dans le constructeur pour la classe:

[!code-cpp[NVC_ATL_COM#29](../atl/codesnippet/cpp/implementing-an-stl-based-collection_6.h)]

Maintenant, vous pouvez tester le code avec le client de votre choix.

## <a name="see-also"></a>Voir aussi

[Collections et énumérateurs](../atl/atl-collections-and-enumerators.md)<br/>
[Échantillon d’ATLCollections](../overview/visual-cpp-samples.md)<br/>
[Classes de politique de copie ATL](../atl/atl-copy-policy-classes.md)
