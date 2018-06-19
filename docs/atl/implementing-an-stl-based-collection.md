---
title: Implémentation d’une Collection de basée sur la bibliothèque Standard C++ | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- ICollectionOnSTLImpl interface
ms.assetid: 6d49f819-1957-4813-b074-3f12c494d8ca
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 14a09f54598b525346a65b56a335711f114878cb
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32359673"
---
# <a name="implementing-a-c-standard-library-based-collection"></a>Implémentation d’un regroupement de bibliothèque C++ Standard
ATL fournit le `ICollectionOnSTLImpl` interface pour vous permettre d’implémenter rapidement des interfaces de collection basées sur la bibliothèque Standard C++ sur vos objets. Pour comprendre le fonctionnement de cette classe, vous allez utiliser un exemple simple (ci-dessous) qui utilise cette classe pour implémenter une collection en lecture seule destinée aux clients Automation.  
  
 L’exemple de code est à partir de la [exemple ATLCollections](../visual-cpp-samples.md).  
  
 Pour effectuer cette procédure, vous allez :  
  
-   [Générer un nouvel objet Simple](#vccongenerating_an_object).  
  
-   [Modifiez le fichier IDL](#vcconedit_the_idl) pour l’interface générée.  
  
-   [Créer cinq typedefs](#vcconstorage_and_exposure_typedefs) décrivant la façon dont les éléments de collection sont stockées et comment ils seront exposés aux clients via les interfaces COM.  
  
-   [Créer deux typedefs pour copier des classes de stratégie](#vcconcopy_classes).  
  
-   [Créer des typedefs pour les implémentations de l’énumérateur et la collection](#vcconenumeration_and_collection).  
  
-   [Modifier le code C++ généré par l’Assistant pour utiliser le typedef de collection](#vcconedit_the_generated_code).  
  
-   [Ajoutez du code pour remplir la collection](#vcconpopulate_the_collection).  
  
##  <a name="vccongenerating_an_object"></a> Génération d’un nouvel objet Simple  
 Créer un nouveau projet, garantir que les attributs sous paramètres de l’Application est désactivée. Utilisez la boîte de dialogue Ajouter une classe ATL et l’Assistant objet Simple pour générer un objet Simple appelé `Words`. Assurez-vous qu’une interface double appelée `IWords` est généré. Objets de la classe générée seront utilisés pour représenter une collection de mots (autrement dit, des chaînes).  
  
##  <a name="vcconedit_the_idl"></a> Modification du fichier IDL  
 Maintenant, ouvrez le fichier IDL et ajoutez les trois propriétés nécessaires pour activer `IWords` dans une interface de collection en lecture seule, comme indiqué ci-dessous :  
  
 [!code-cpp[NVC_ATL_COM#24](../atl/codesnippet/cpp/implementing-an-stl-based-collection_1.idl)]  
  
 Il s’agit de la forme standard pour une interface de collection en lecture seule conçue avec des clients Automation à l’esprit. Les commentaires numérotés dans cette définition d’interface correspondent aux commentaires ci-dessous :  
  
1.  Interfaces de collection sont généralement doubles, car les clients Automation accède à la `_NewEnum` propriété via **IDispatch::Invoke**. Toutefois, les clients Automation peuvent accéder aux méthodes restantes via la vtable, les interfaces doubles sont préférables aux dispinterfaces.  
  
2.  Si une interface double ou une dispinterface n’est pas étendue au moment de l’exécution (autrement dit, vous ne fournir des méthodes supplémentaires ou des propriétés via **IDispatch::Invoke**), vous devez appliquer le **nonextensible** attribut votre définition. Cet attribut permet aux clients Automation d’effectuer la vérification du code au moment de la compilation. Dans ce cas, l’interface ne doit pas être étendu.  
  
3.  Le DISPID correct est important si vous souhaitez que les clients Automation d’être en mesure d’utiliser cette propriété. (Notez qu’il y a qu’un seul trait de soulignement dans **DISPID_NEWENUM**.)  
  
4.  Vous pouvez fournir n’importe quelle valeur comme DISPID de la **élément** propriété. Toutefois, **élément** utilise généralement **DISPID_VALUE** afin de faciliter la propriété par défaut de la collection. Ainsi, les clients Automation faire référence à la propriété sans la nommer explicitement.  
  
5.  Le type de données utilisé pour la valeur de retour de la **élément** propriété est le type de l’élément stocké dans la collection, comme les clients COM sont concernés. L’interface retourne des chaînes, vous devez utiliser le type de chaîne COM standard, `BSTR`. Vous pouvez stocker les données dans un format différent en interne comme vous le verrez bientôt.  
  
6.  La valeur utilisée pour le DISPID de la **nombre** propriété est arbitraire. Il n’existe aucun DISPID standard pour cette propriété.  
  
##  <a name="vcconstorage_and_exposure_typedefs"></a> Création de Typedefs pour le stockage et l’exposition  
 Une fois que l’interface de collection est défini, vous devez décider comment les données doivent être stockées et comment les données sont exposées via l’énumérateur.  
  
 Les réponses à ces questions peuvent être fournies sous la forme d’un nombre de typedefs, que vous pouvez ajouter au début du fichier d’en-tête pour votre classe nouvellement créé :  
  
 [!code-cpp[NVC_ATL_COM#25](../atl/codesnippet/cpp/implementing-an-stl-based-collection_2.h)]  
  
 Dans ce cas, vous stockerez les données comme un **std::vector** de **std::string**s. **std::Vector** est une classe de conteneur de bibliothèque C++ Standard qui se comporte comme un tableau managé. **std::String** est la classe de chaîne de la bibliothèque Standard C++. Ces classes vous permet de travailler avec une collection de chaînes.  
  
 Étant donné que la prise en charge de Visual Basic est essentiel à la réussite de cette interface, l’énumérateur retourné par la `_NewEnum` propriété doit prendre en charge la **IEnumVARIANT** interface. Il s’agit de la seule interface d’énumérateur compris par Visual Basic.  
  
##  <a name="vcconcopy_classes"></a> Création de Typedefs pour les Classes de stratégies de copie  
 Les typedefs créés jusqu'à présent fournissent toutes les informations dont vous avez besoin créer d’autres typedefs pour les classes de copie qui seront utilisées par l’énumérateur et la collection :  
  
 [!code-cpp[NVC_ATL_COM#26](../atl/codesnippet/cpp/implementing-an-stl-based-collection_3.h)]  
  
 Dans cet exemple, vous pouvez utiliser personnalisé `GenericCopy` classe définie dans VCUE_Copy.h et VCUE_CopyString.h à partir de la [ATLCollections](../visual-cpp-samples.md) exemple. Vous pouvez utiliser cette classe dans un autre code, mais vous devrez peut-être définir d’autres spécialisations de `GenericCopy` pour prendre en charge les types de données utilisés dans vos propres collections. Pour plus d’informations, consultez [Classes de stratégies de copie ATL](../atl/atl-copy-policy-classes.md).  
  
##  <a name="vcconenumeration_and_collection"></a> Création de Typedefs pour l’énumération et la Collection  
 Maintenant tous les paramètres du modèle nécessaires pour spécialiser le `CComEnumOnSTL` et `ICollectionOnSTLImpl` dans ce cas, les classes ont été fournis sous la forme de typedefs. Pour simplifier l’utilisation des spécialisations, créez deux typedefs supplémentaires, comme indiqué ci-dessous :  
  
 [!code-cpp[NVC_ATL_COM#27](../atl/codesnippet/cpp/implementing-an-stl-based-collection_4.h)]  
  
 Maintenant `CollectionType` est un synonyme pour une spécialisation de `ICollectionOnSTLImpl` qui implémente le `IWords` interface défini précédemment et fournit un énumérateur qui prend en charge **IEnumVARIANT**.  
  
##  <a name="vcconedit_the_generated_code"></a> Modifiez le Code généré par l’Assistant  
 Maintenant, vous devez dériver `CWords` à partir de l’implémentation d’interface représentée par le `CollectionType` typedef plutôt que `IWords`, comme indiqué ci-dessous :  
  
 [!code-cpp[NVC_ATL_COM#28](../atl/codesnippet/cpp/implementing-an-stl-based-collection_5.h)]  
  
##  <a name="vcconpopulate_the_collection"></a> Ajout de Code pour remplir la Collection  
 La seule chose qui reste est à remplir le vecteur avec des données. Dans cet exemple simple, vous pouvez ajouter quelques mots à la collection dans le constructeur de la classe :  
  
 [!code-cpp[NVC_ATL_COM#29](../atl/codesnippet/cpp/implementing-an-stl-based-collection_6.h)]  
  
 Maintenant, vous pouvez tester le code avec le client de votre choix.  
  
## <a name="see-also"></a>Voir aussi  
 [Collections et énumérateurs](../atl/atl-collections-and-enumerators.md)   
 [ATLCollections, exemple](../visual-cpp-samples.md)   
 [Classes de stratégies de copie ATL](../atl/atl-copy-policy-classes.md)

