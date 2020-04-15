---
title: Collections
ms.date: 11/04/2016
helpviewer_keywords:
- MFC, collections
- arrays [MFC], classes
- MFC collection classes
- shapes, collection
- collection classes [MFC], MFC
- collections, about collections
- array templates [MFC]
- collection classes [MFC], template-based
- collection classes [MFC], about collection classes
- collection classes [MFC], maps
- collection classes [MFC], arrays
- shapes
- collection classes [MFC], lists
- collection classes [MFC], shapes
ms.assetid: 02586e4c-851d-41d0-a722-feb11c17c74c
ms.openlocfilehash: 3fba3a3c6cd3fecbda7f46575b1d72c450c44019
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81361872"
---
# <a name="collections"></a>Collections

La bibliothèque MFC fournit des classes de collection pour gérer des groupes d’objets. Ces classes sont de deux types :

- [Classes de collection créées à partir de modèles C++](#_core_the_template_based_collection_classes)

- [Classes de collection non créées à partir de modèles C++](#_core_the_collection_classes_not_based_on_templates)

> [!NOTE]
> Si votre code utilise déjà les classes de collection basées sur des modèles, vous pouvez continuer à les utiliser. Si vous spécifiez de nouvelles classes de collection de type sécurisé pour vos propres types de données, nous vous recommandons d'utiliser les classes les plus récentes basées sur des modèles.

## <a name="collection-shapes"></a><a name="_core_collection_shapes"></a>Formes de collection

Une classe de collection est caractérisée par sa "forme" et par les types de ses éléments. La forme fait référence à la façon dont les objets sont organisés et stockés par la collection. MFC fournit trois formes de base de collection : listes, tableaux et mappages (également appelés dictionnaires). Choisissez la forme de collection qui est la plus adaptée à votre problème de programmation particulier.

Chacune des trois formes de collection est décrite brièvement plus loin dans cette rubrique. Pour comparer les caractéristiques des formes pour vous aider à décider ce qui est le mieux pour votre programme, consultez [recommandations pour choisir une classe de collection](../mfc/recommendations-for-choosing-a-collection-class.md).

- List

   La classe de liste fournit une liste triée et non indexée d'éléments, implémentée comme une liste doublement chaînée. Une liste possède une "tête" et une "queue", et ajouter ou supprimer des éléments de la tête ou de la queue, ou insérer ou supprimer des éléments au milieu, est très rapide.

- Array

   La classe de tableau fournit un tableau d'objets classés, ordonnés et indexés par des entiers.

- Mappage (également appelé dictionnaire)

   Un mappage est une collection qui associe un objet principal à un objet de valeur.

## <a name="the-template-based-collection-classes"></a><a name="_core_the_template_based_collection_classes"></a>Les classes de collection basées sur le modèle

La façon la plus simple d’implémenter une collection de type sécurisé qui contient des objets de tout type est d’utiliser l’une des classes MFC basées sur un modèle. Pour des exemples de ces classes, voir l’échantillon MFC [COLLECT](../overview/visual-cpp-samples.md).

Le tableau suivant répertorie les classes de collection MFC basées sur des modèles :

### <a name="collection-template-classes"></a>Classes de modèle de collections

|Contenu des collections|Tableaux|Listes|Cartes|
|-------------------------|------------|-----------|----------|
|Collections d’objets de n’importe quel type|`CArray`|`CList`|`CMap`|
|Collections de pointeurs vers des objets de n’importe quel type|`CTypedPtrArray`|`CTypedPtrList`|`CTypedPtrMap`|

## <a name="the-collection-classes-not-based-on-templates"></a><a name="_core_the_collection_classes_not_based_on_templates"></a>Les classes de collection ne sont pas basées sur des modèles

Si votre application utilise déjà les classes MFC de collection qui ne se basent pas sur des modèles, vous pouvez continuer à les utiliser. Toutefois, pour les nouvelles collections, nous vous recommandons d’utiliser les classes basées sur des modèles. Le tableau suivant répertorie les classes de collection MFC qui ne sont pas basées sur des modèles.

### <a name="nontemplate-collection-classes"></a>Classes de collections non basées sur des modèles

|Tableaux|Listes|Cartes|
|------------|-----------|----------|
|`CObArray`|`CObList`|`CMapPtrToWord`|
|`CByteArray`|`CPtrList`|`CMapPtrToPtr`|
|`CDWordArray`|`CStringList`|`CMapStringToOb`|
|`CPtrArray`||`CMapStringToPtr`|
|`CStringArray`||`CMapStringToString`|
|`CWordArray`||`CMapWordToOb`|
|`CUIntArray`||`CMapWordToPtr`|

La table caractéristiques des classes de collection MFC dans [Recommandations pour le choix d’une classe de collection](../mfc/recommendations-for-choosing-a-collection-class.md) décrit les classes de collecte MFC en termes de ces caractéristiques (autres que la forme) :

- Si la classe utilise des modèles C++

- Si les éléments stockés dans la collection peuvent être sérialisés

- Si les éléments stockés dans la collection peuvent faire l'objet d'un dump pour effectuer des diagnostics

- Si la collection est de type sécurisé

### <a name="what-do-you-want-to-do"></a>Tu veux faire quoi

#### <a name="general-collection-class-tasks"></a>Tâches de classe de collection générales

- [Recommandations relatives au choix d’une classe de collection](../mfc/recommendations-for-choosing-a-collection-class.md)

- [Guide pratique pour définir une collection de type sécurisé](../mfc/how-to-make-a-type-safe-collection.md)

- [Création de collections de piles et de files d’attente](../mfc/creating-stack-and-queue-collections.md)

- [CArray::Ajouter](../mfc/reference/carray-class.md#add)

#### <a name="template-based-collection-class-tasks"></a>Tâches de classe de collection basées sur un modèle

- [Catégories basées sur des modèles](../mfc/template-based-classes.md)

#### <a name="accessing-the-members-of-a-collection-template-based-or-not"></a>Accès aux membres d'une collection (basée sur un modèle ou non)

- [Accès à tous les membres d’une collection](../mfc/accessing-all-members-of-a-collection.md)

- [Suppression de tous les objets d’une collection CObject](../mfc/deleting-all-objects-in-a-cobject-collection.md)

## <a name="see-also"></a>Voir aussi

[Concepts liés à la](../mfc/mfc-concepts.md)<br/>
[Rubriques MFC générales](../mfc/general-mfc-topics.md)
