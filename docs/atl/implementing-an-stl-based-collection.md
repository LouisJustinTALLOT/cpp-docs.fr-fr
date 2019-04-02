---
title: Implémentation d’une Collection de basée sur la bibliothèque Standard C++
ms.date: 11/04/2016
helpviewer_keywords:
- ICollectionOnSTLImpl interface
ms.assetid: 6d49f819-1957-4813-b074-3f12c494d8ca
ms.openlocfilehash: 609ec2547cf7a8ab93ef757f7a8e460542c9de28
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/01/2019
ms.locfileid: "58779246"
---
# <a name="implementing-a-c-standard-library-based-collection"></a>Implémentation d’une Collection de basée sur la bibliothèque Standard C++

ATL fournit le `ICollectionOnSTLImpl` interface pour vous permettre d’implémenter rapidement des interfaces de collection basées sur la bibliothèque Standard C++ sur vos objets. Pour comprendre le fonctionne de cette classe, vous travaillerez avec un exemple simple (ci-dessous) qui utilise cette classe pour implémenter une collection en lecture seule destinée aux clients Automation.

L’exemple de code présente le [exemple ATLCollections](../overview/visual-cpp-samples.md).

Pour effectuer cette procédure, vous allez :

- [Générer un nouvel objet Simple](#vccongenerating_an_object).

- [Modifiez le fichier IDL](#vcconedit_the_idl) pour l’interface générée.

- [Créer cinq typedefs](#vcconstorage_and_exposure_typedefs) décrivant la façon dont les éléments de collection sont stockés et comment ils seront exposés aux clients via les interfaces COM.

- [Créer des classes de stratégie deux typedefs pour copie](#vcconcopy_classes).

- [Créer des typedefs pour les implémentations de l’énumérateur et collection](#vcconenumeration_and_collection).

- [Modifier le code C++ généré par l’Assistant pour utiliser le typedef de collection](#vcconedit_the_generated_code).

- [Ajoutez du code pour remplir la collection](#vcconpopulate_the_collection).

##  <a name="vccongenerating_an_object"></a> Génération d’un nouvel objet Simple

Créer un nouveau projet, en garantissant que les attributs sous paramètres de l’Application est désactivée. Utilisez la boîte de dialogue Ajouter une classe ATL et l’Assistant objet Simple pour générer un objet Simple appelé `Words`. Assurez-vous qu’une interface double appelée `IWords` est généré. Objets de la classe générée seront utilisés pour représenter une collection de mots (autrement dit, des chaînes).

##  <a name="vcconedit_the_idl"></a> Modification du fichier IDL

À présent, ouvrez le fichier IDL et ajoutez les trois propriétés nécessaires pour activer `IWords` dans une interface de collection en lecture seule, comme indiqué ci-dessous :

[!code-cpp[NVC_ATL_COM#24](../atl/codesnippet/cpp/implementing-an-stl-based-collection_1.idl)]

Il s’agit de la forme standard pour une interface de collection en lecture seule conçue avec les clients Automation à l’esprit. Les commentaires numérotés dans cette définition d’interface correspondent aux commentaires ci-dessous :

1. Interfaces de collection sont généralement à doubles, car les clients Automation accède à la `_NewEnum` propriété via `IDispatch::Invoke`. Toutefois, les clients Automation peuvent accéder les méthodes restantes via la vtable, les interfaces doubles sont préférables aux dispinterfaces.

1. Si une interface double ou une dispinterface n’est pas étendue au moment de l’exécution (autrement dit, vous ne fournissez des méthodes supplémentaires ou des propriétés via `IDispatch::Invoke`), vous devez appliquer le **nonextensible** à votre définition d’attribut. Cet attribut permet aux clients Automation d’effectuer la vérification du code complète au moment de la compilation. Dans ce cas, l’interface ne doit pas être étendu.

1. Le DISPID correct est important si vous souhaitez que les clients Automation d’être en mesure d’utiliser cette propriété. (Notez qu’il n'existe qu’un seul trait de soulignement dans DISPID_NEWENUM.)

1. Vous pouvez fournir n’importe quelle valeur en tant que le DISPID de la `Item` propriété. Toutefois, `Item` utilise DISPID_VALUE comme pour le rendre la propriété par défaut de la collection. Cela permet aux clients Automation de font référence à la propriété sans la nommer explicitement.

1. Le type de données utilisé pour la valeur de retour de la `Item` propriété est le type de l’élément stocké dans la collection, comme les clients COM sont concernés. L’interface retourne des chaînes, vous devez utiliser le type de chaîne COM standard, BSTR. Vous pouvez stocker les données dans un format différent en interne comme vous le verrez bientôt.

1. La valeur utilisée pour le DISPID de la `Count` propriété est totalement aléatoires. Il n’existe aucun DISPID standard pour cette propriété.

##  <a name="vcconstorage_and_exposure_typedefs"></a> Création de Typedefs pour le stockage et l’exposition

Une fois que l’interface de collection est défini, vous devez déterminer comment les données doivent être stockées et comment les données seront exposées par le biais de l’énumérateur.

Les réponses à ces questions peuvent être fournies sous la forme d’un nombre de typedefs, que vous pouvez ajouter au début du fichier d’en-tête pour votre classe nouvellement créé :

[!code-cpp[NVC_ATL_COM#25](../atl/codesnippet/cpp/implementing-an-stl-based-collection_2.h)]

Dans ce cas, vous stockerez les données en tant qu’un **std::vector** de **std::string**s. **std::Vector** est une classe de conteneur de bibliothèque C++ Standard qui se comporte comme un tableau managé. **std::String** est la classe de chaîne de la bibliothèque Standard C++. Ces classes vous permettent de facilement travailler avec une collection de chaînes.

Étant donné que la prise en charge de Visual Basic est essentiel à la réussite de cette interface, l’énumérateur retourné par la `_NewEnum` propriété doit prendre en charge la `IEnumVARIANT` interface. Il s’agit de la seule interface d’énumérateur compris par Visual Basic.

##  <a name="vcconcopy_classes"></a> Création de Typedefs pour les Classes de stratégie de copie

Les typedefs que vous avez créé jusqu'à présent fournir toutes les informations que vous avez besoin de créer de nouvelles typedefs pour les classes de copie qui seront utilisées par l’énumérateur et la collection :

[!code-cpp[NVC_ATL_COM#26](../atl/codesnippet/cpp/implementing-an-stl-based-collection_3.h)]

Dans cet exemple, vous pouvez utiliser personnalisé `GenericCopy` classe définie dans VCUE_Copy.h et VCUE_CopyString.h à partir de la [ATLCollections](../overview/visual-cpp-samples.md) exemple. Vous pouvez utiliser cette classe dans un autre code, mais vous devrez peut-être définir d’autres spécialisations de `GenericCopy` pour prendre en charge les types de données utilisés dans vos propres regroupements. Pour plus d’informations, consultez [Classes de stratégies de copie ATL](../atl/atl-copy-policy-classes.md).

##  <a name="vcconenumeration_and_collection"></a> Création de Typedefs pour l’énumération et la Collection

Maintenant tous les paramètres du modèle nécessaires pour spécialiser le `CComEnumOnSTL` et `ICollectionOnSTLImpl` dans ce cas, les classes ont été fournis sous la forme de typedefs. Pour simplifier l’utilisation des spécialisations, créez deux typedefs supplémentaires, comme indiqué ci-dessous :

[!code-cpp[NVC_ATL_COM#27](../atl/codesnippet/cpp/implementing-an-stl-based-collection_4.h)]

Maintenant `CollectionType` est un synonyme pour une spécialisation de `ICollectionOnSTLImpl` qui implémente le `IWords` interface définies plus tôt et fournit un énumérateur qui prend en charge `IEnumVARIANT`.

##  <a name="vcconedit_the_generated_code"></a> Modification du Code généré par l’Assistant

Maintenant vous devez dériver `CWords` à partir de l’implémentation d’interface représentée par le `CollectionType` typedef plutôt que `IWords`, comme illustré ci-dessous :

[!code-cpp[NVC_ATL_COM#28](../atl/codesnippet/cpp/implementing-an-stl-based-collection_5.h)]

##  <a name="vcconpopulate_the_collection"></a> Ajout de Code pour remplir la Collection

La seule chose qui reste consiste à remplir le vecteur avec des données. Dans cet exemple simple, vous pouvez ajouter quelques mots à la collection dans le constructeur de la classe :

[!code-cpp[NVC_ATL_COM#29](../atl/codesnippet/cpp/implementing-an-stl-based-collection_6.h)]

Vous pouvez maintenant tester le code avec le client de votre choix.

## <a name="see-also"></a>Voir aussi

[Collections et énumérateurs](../atl/atl-collections-and-enumerators.md)<br/>
[ATLCollections, exemple](../overview/visual-cpp-samples.md)<br/>
[Classes de stratégies de copie ATL](../atl/atl-copy-policy-classes.md)
