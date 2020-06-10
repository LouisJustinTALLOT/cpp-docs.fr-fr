---
title: 'Comment : créer une table des messages pour une classe de modèle'
ms.date: 11/04/2016
helpviewer_keywords:
- template classes [MFC], creating message maps
- message maps [MFC], template classes
ms.assetid: 4e7e24f8-06df-4b46-82aa-7435c8650de3
ms.openlocfilehash: 65ddc77b4e8fd466c7d651e54e93a504b4858da1
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84620066"
---
# <a name="how-to-create-a-message-map-for-a-template-class"></a>Comment : créer une table des messages pour une classe de modèle

La création d'une table des messages dans MFC est un moyen efficace pour diriger les messages Windows vers une instance d'objet appropriée C++. Les exemples de cibles de table des messages MFC comprennent des classes d'application, des classes de document et de vue, des classes de contrôle, etc.

Les tables des messages MFC traditionnelles sont déclarées à l’aide de la macro [BEGIN_MESSAGE_MAP](reference/message-map-macros-mfc.md#begin_message_map) pour déclarer le début de la table des messages, une entrée de macro pour chaque méthode de la classe de gestionnaire de messages, et enfin la macro [END_MESSAGE_MAP](reference/message-map-macros-mfc.md#end_message_map) pour déclarer la fin de la table des messages.

L’une des limitations de la macro [BEGIN_MESSAGE_MAP](reference/message-map-macros-mfc.md#begin_message_map) se produit lorsqu’elle est utilisée conjointement avec une classe contenant des arguments template. Si elle est utilisée avec une classe de modèle, la macro entraînera une erreur de compilation en raison des paramètres de modèle manquants pendant l'expansion macro. La macro [BEGIN_TEMPLATE_MESSAGE_MAP](reference/message-map-macros-mfc.md#begin_template_message_map) a été conçue pour permettre aux classes contenant un argument template unique de déclarer leurs propres tables de messages.

## <a name="example"></a>Exemple

Prenons un exemple dans lequel la classe MFC [CListBox](reference/clistbox-class.md) est étendue pour assurer la synchronisation avec une source de données externe. La classe fictive `CSyncListBox` est déclarée comme suit :

[!code-cpp[NVC_MFC_CListBox#42](codesnippet/cpp/how-to-create-a-message-map-for-a-template-class_1.h)]

La `CSyncListBox` classe est basée sur un modèle unique qui décrit la source de données avec laquelle elle sera synchronisée. Elle déclare également trois méthodes qui feront partie de la table des messages de la classe : `OnPaint` , `OnDestroy` et `OnSynchronize` . La `OnSynchronize` méthode est implémentée comme suit :

[!code-cpp[NVC_MFC_CListBox#43](codesnippet/cpp/how-to-create-a-message-map-for-a-template-class_2.cpp)]

L’implémentation ci-dessus permet `CSyncListBox` à la classe d’être spécialisée sur tout type de classe qui implémente la `GetCount` méthode, par exemple `CArray` ,, `CList` et `CMap` . La `StringizeElement` fonction est une fonction de modèle prototypée par ce qui suit :

[!code-cpp[NVC_MFC_CListBox#44](codesnippet/cpp/how-to-create-a-message-map-for-a-template-class_3.cpp)]

Normalement, la table des messages pour cette classe est définie comme suit :

```cpp
BEGIN_MESSAGE_MAP(CSyncListBox, CListBox)
  ON_WM_PAINT()
  ON_WM_DESTROY()
  ON_MESSAGE(LBN_SYNCHRONIZE, OnSynchronize)
END_MESSAGE_MAP()
```

où **LBN_SYNCHRONIZE** est un message utilisateur personnalisé défini par l’application, par exemple :

[!code-cpp[NVC_MFC_CListBox#45](codesnippet/cpp/how-to-create-a-message-map-for-a-template-class_4.cpp)]

L’Explorateur de macros ci-dessus ne se compile pas, en raison du fait que la spécification de modèle pour la `CSyncListBox` classe est manquante pendant l’expansion macro. La macro **BEGIN_TEMPLATE_MESSAGE_MAP** résout cela en incorporant le paramètre de modèle spécifié dans l’Explorateur de macros développée. La table des messages pour cette classe est :

[!code-cpp[NVC_MFC_CListBox#46](codesnippet/cpp/how-to-create-a-message-map-for-a-template-class_5.cpp)]

L’exemple suivant illustre l’utilisation de la `CSyncListBox` classe à l’aide d’un `CStringList` objet :

[!code-cpp[NVC_MFC_CListBox#47](codesnippet/cpp/how-to-create-a-message-map-for-a-template-class_6.cpp)]

Pour terminer le test, la `StringizeElement` fonction doit être spécialisée pour fonctionner avec la `CStringList` classe :

[!code-cpp[NVC_MFC_CListBox#48](codesnippet/cpp/how-to-create-a-message-map-for-a-template-class_7.cpp)]

## <a name="see-also"></a>Voir aussi

[BEGIN_TEMPLATE_MESSAGE_MAP](reference/message-map-macros-mfc.md#begin_template_message_map)<br/>
[Gestion et mappage des messages](message-handling-and-mapping.md)
