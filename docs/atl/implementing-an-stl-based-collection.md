---
description: 'En savoir plus sur : implémentation d’une collection de Library-Based standard C++'
title: Implémentation d’une collection Library-Based standard C++
ms.date: 11/04/2016
helpviewer_keywords:
- ICollectionOnSTLImpl interface
ms.assetid: 6d49f819-1957-4813-b074-3f12c494d8ca
ms.openlocfilehash: 4a403885a6fe66bf8e8578deeab05c7fc08e88a5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97152852"
---
# <a name="implementing-a-c-standard-library-based-collection"></a>Implémentation d’une collection Library-Based standard C++

ATL fournit l' `ICollectionOnSTLImpl` interface pour vous permettre d’implémenter rapidement des interfaces de collection basées sur la bibliothèque standard C++ sur vos objets. Pour comprendre le fonctionnement de cette classe, vous allez utiliser un exemple simple (ci-dessous) qui utilise cette classe pour implémenter une collection en lecture seule destinée aux clients Automation.

L’exemple de code provient de l' [exemple ATLCollections](../overview/visual-cpp-samples.md).

Pour effectuer cette procédure, vous allez :

- [Générez un nouvel objet simple](#vccongenerating_an_object).

- [Modifiez le fichier IDL](#vcconedit_the_idl) de l’interface générée.

- [Créez cinq typedefs](#vcconstorage_and_exposure_typedefs) qui décrivent comment les éléments de la collection sont stockés et comment ils seront exposés aux clients via des interfaces com.

- [Créez deux typedefs pour les classes de stratégie de copie](#vcconcopy_classes).

- [Créez des typedefs pour les implémentations d’énumérateur et de collection](#vcconenumeration_and_collection).

- [Modifiez le code C++ généré par l’Assistant pour utiliser le typedef de collection](#vcconedit_the_generated_code).

- [Ajoutez du code pour remplir la collection](#vcconpopulate_the_collection).

## <a name="generating-a-new-simple-object"></a><a name="vccongenerating_an_object"></a> Génération d’un nouvel objet simple

Créez un projet, en vous assurant que la zone attributs sous paramètres de l’application est désactivée. Utilisez la boîte de dialogue Ajouter une classe ATL et l’Assistant Ajouter un objet simple pour générer un objet simple appelé `Words` . Assurez-vous qu’une interface double appelée `IWords` est générée. Les objets de la classe générée seront utilisés pour représenter une collection de mots (autrement dit, des chaînes).

## <a name="editing-the-idl-file"></a><a name="vcconedit_the_idl"></a> Modification du fichier IDL

À présent, ouvrez le fichier IDL et ajoutez les trois propriétés nécessaires à l’activation d' `IWords` une interface de collection en lecture seule, comme indiqué ci-dessous :

[!code-cpp[NVC_ATL_COM#24](../atl/codesnippet/cpp/implementing-an-stl-based-collection_1.idl)]

Il s’agit du formulaire standard pour une interface de collection en lecture seule conçue avec les clients Automation à l’esprit. Les commentaires numérotés dans cette définition d’interface correspondent aux commentaires ci-dessous :

1. Les interfaces de collection sont généralement doubles, car les clients Automation accèdent à la `_NewEnum` propriété via `IDispatch::Invoke` . Toutefois, les clients Automation peuvent accéder aux autres méthodes via la vtable, de sorte que les interfaces doubles sont préférables aux dispinterfaces.

1. Si une interface double ou une dispinterface ne sont pas étendues au moment de l’exécution (autrement dit, si vous ne fournissez pas de méthodes ou de propriétés supplémentaires via `IDispatch::Invoke` ), vous devez appliquer l’attribut non **extensible** à votre définition. Cet attribut permet aux clients Automation d’effectuer une vérification de code complète au moment de la compilation. Dans ce cas, l’interface ne doit pas être étendue.

1. Le DISPID correct est important si vous souhaitez que les clients Automation soient en mesure d’utiliser cette propriété. (Notez qu’il n’y a qu’un seul trait de soulignement dans DISPID_NEWENUM.)

1. Vous pouvez fournir n’importe quelle valeur comme DISPID de la `Item` propriété. Toutefois, `Item` utilise généralement DISPID_VALUE pour en faire la propriété par défaut de la collection. Cela permet aux clients Automation de faire référence à la propriété sans la nommer explicitement.

1. Le type de données utilisé pour la valeur de retour de la `Item` propriété est le type de l’élément stocké dans la collection en ce qui concerne les clients com. L’interface retourne des chaînes. vous devez donc utiliser le type de chaîne COM standard, BSTR. Vous pouvez stocker les données dans un format différent en interne, comme vous le verrez bientôt.

1. La valeur utilisée pour le DISPID de la `Count` propriété est complètement arbitraire. Il n’existe aucun DISPID standard pour cette propriété.

## <a name="creating-typedefs-for-storage-and-exposure"></a><a name="vcconstorage_and_exposure_typedefs"></a> Création de typedefs pour le stockage et l’exposition

Une fois l’interface de collection définie, vous devez décider de la façon dont les données seront stockées et de la façon dont les données sont exposées via l’énumérateur.

Les réponses à ces questions peuvent être fournies sous la forme d’un certain nombre de typedefs, que vous pouvez ajouter vers le haut du fichier d’en-tête pour la classe nouvellement créée :

[!code-cpp[NVC_ATL_COM#25](../atl/codesnippet/cpp/implementing-an-stl-based-collection_2.h)]

Dans ce cas, vous allez stocker les données sous la forme d’un **std :: Vector** de **std :: String** s. **std :: Vector** est une classe de conteneur de bibliothèque standard C++ qui se comporte comme un tableau managé. **std :: String** est la classe de chaîne de la bibliothèque standard C++. Ces classes facilitent l’utilisation d’une collection de chaînes.

Étant donné que la prise en charge de Visual Basic est vitale pour la réussite de cette interface, l’énumérateur retourné par la `_NewEnum` propriété doit prendre en charge l' `IEnumVARIANT` interface. Il s’agit de la seule interface d’énumérateur comprise par Visual Basic.

## <a name="creating-typedefs-for-copy-policy-classes"></a><a name="vcconcopy_classes"></a> Création de typedefs pour les classes de stratégie de copie

Les typedefs que vous avez créés jusqu’à présent fournissent toutes les informations dont vous avez besoin pour créer des typedefs supplémentaires pour les classes de copie qui seront utilisées par l’énumérateur et la collection :

[!code-cpp[NVC_ATL_COM#26](../atl/codesnippet/cpp/implementing-an-stl-based-collection_3.h)]

Dans cet exemple, vous pouvez utiliser la `GenericCopy` classe personnalisée définie dans VCUE_Copy. h et VCUE_CopyString. h à partir de l’exemple [ATLCollections](../overview/visual-cpp-samples.md) . Vous pouvez utiliser cette classe dans un autre code, mais vous devrez peut-être définir d’autres spécialisations de `GenericCopy` pour prendre en charge les types de données utilisés dans vos propres collections. Pour plus d’informations, consultez [classes de stratégie de copie ATL](../atl/atl-copy-policy-classes.md).

## <a name="creating-typedefs-for-enumeration-and-collection"></a><a name="vcconenumeration_and_collection"></a> Création de typedefs pour l’énumération et la collection

Désormais, tous les paramètres de modèle nécessaires à la spécialisation des `CComEnumOnSTL` `ICollectionOnSTLImpl` classes et pour cette situation ont été fournis sous la forme de typedefs. Pour simplifier l’utilisation des spécialisations, créez deux typedefs supplémentaires comme indiqué ci-dessous :

[!code-cpp[NVC_ATL_COM#27](../atl/codesnippet/cpp/implementing-an-stl-based-collection_4.h)]

`CollectionType`Est maintenant un synonyme d’une spécialisation de `ICollectionOnSTLImpl` qui implémente l' `IWords` interface définie précédemment et fournit un énumérateur qui prend en charge `IEnumVARIANT` .

## <a name="editing-the-wizard-generated-code"></a><a name="vcconedit_the_generated_code"></a> Modification du code Wizard-Generated

À présent, vous devez dériver `CWords` de l’implémentation d’interface représentée par le `CollectionType` typedef plutôt que `IWords` , comme indiqué ci-dessous :

[!code-cpp[NVC_ATL_COM#28](../atl/codesnippet/cpp/implementing-an-stl-based-collection_5.h)]

## <a name="adding-code-to-populate-the-collection"></a><a name="vcconpopulate_the_collection"></a> Ajout de code pour remplir la collection

La seule chose qui reste est de remplir le vecteur avec des données. Dans cet exemple simple, vous pouvez ajouter quelques mots à la collection dans le constructeur de la classe :

[!code-cpp[NVC_ATL_COM#29](../atl/codesnippet/cpp/implementing-an-stl-based-collection_6.h)]

Vous pouvez maintenant tester le code avec le client de votre choix.

## <a name="see-also"></a>Voir aussi

[Collections et énumérateurs](../atl/atl-collections-and-enumerators.md)<br/>
[Exemple ATLCollections](../overview/visual-cpp-samples.md)<br/>
[Classes de stratégie de copie ATL](../atl/atl-copy-policy-classes.md)
