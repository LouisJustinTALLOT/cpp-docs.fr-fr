---
title: 'Comment : créer une table des messages pour une classe de modèle | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- template classes [MFC], creating message maps
- message maps [MFC], template classes
ms.assetid: 4e7e24f8-06df-4b46-82aa-7435c8650de3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6781ca14b174608a815a0300750dd6a3d9aa96bb
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33354778"
---
# <a name="how-to-create-a-message-map-for-a-template-class"></a>Comment : créer une table des messages pour une classe de modèle
La création d'une table des messages dans MFC est un moyen efficace pour diriger les messages Windows vers une instance d'objet appropriée C++. Les exemples de cibles de table des messages MFC comprennent des classes d'application, des classes de document et de vue, des classes de contrôle, etc.  
  
 Tables des messages MFC classiques sont déclarés à l’aide de la [BEGIN_MESSAGE_MAP](reference/message-map-macros-mfc.md#begin_message_map) macro pour déclarer le début de la table des messages, une entrée de macro pour chaque méthode de classe de gestionnaire de messages et enfin la [END_MESSAGE_MAP](reference/message-map-macros-mfc.md#end_message_map)macro pour déclarer la fin de la table des messages.  
  
 Une limitation avec le [BEGIN_MESSAGE_MAP](reference/message-map-macros-mfc.md#begin_message_map) macro se produit lorsqu’il est utilisé conjointement avec une classe contenant les arguments de modèle. Si elle est utilisée avec une classe de modèle, la macro entraînera une erreur au moment de la compilation en raison des paramètres de modèle manquants pendant l’expansion macro. Le [BEGIN_TEMPLATE_MESSAGE_MAP](reference/message-map-macros-mfc.md#begin_template_message_map) macro a été conçu pour les classes contenant un argument unique de modèle pour déclarer leurs propres messages mappe.  
  
## <a name="example"></a>Exemple  
 Prenons un exemple où la bibliothèque MFC [CListBox](../mfc/reference/clistbox-class.md) classe est étendue pour assurer la synchronisation avec une source de données externe. Le fictive **CSyncListBox** classe est déclarée comme suit :  
  
 [!code-cpp[NVC_MFC_CListBox#42](../mfc/codesnippet/cpp/how-to-create-a-message-map-for-a-template-class_1.h)]  
  
 Le **CSyncListBox** classe est basé sur un modèle sur un seul type qui décrit le synchronise avec la source de données. Elle déclare également trois méthodes qui participeront à la table des messages de la classe : **OnPaint**, **OnDestroy**, et **OnSynchronize**. Le **OnSynchronize** méthode est implémentée comme suit :  
  
 [!code-cpp[NVC_MFC_CListBox#43](../mfc/codesnippet/cpp/how-to-create-a-message-map-for-a-template-class_2.cpp)]  
  
 L’implémentation ci-dessus le **CSyncListBox** classe spécialisés sur n’importe quel type de classe qui implémente le **GetCount** (méthode), tel que **CArray**, **CList**, et **CMap**. Le **StringizeElement** fonction est une fonction de modèle prototypée par ce qui suit :  
  
 [!code-cpp[NVC_MFC_CListBox#44](../mfc/codesnippet/cpp/how-to-create-a-message-map-for-a-template-class_3.cpp)]  
  
 Normalement, la table des messages pour cette classe est définie comme suit :  
  
 `BEGIN_MESSAGE_MAP(CSyncListBox, CListBox)`  
  
 `ON_WM_PAINT()`  
  
 `ON_WM_DESTROY()`  
  
 `ON_MESSAGE(LBN_SYNCHRONIZE, OnSynchronize)`  
  
 `END_MESSAGE_MAP()`  
  
 où **LBN_SYNCHRONIZE** est un message utilisateur personnalisé défini par l’application, telles que :  
  
 [!code-cpp[NVC_MFC_CListBox#45](../mfc/codesnippet/cpp/how-to-create-a-message-map-for-a-template-class_4.cpp)]  
  
 La carte de macro ci-dessus ne compilera pas, dû au fait que la spécification du modèle pour le **CSyncListBox** classe sera manquant pendant l’expansion macro. Le **BEGIN_TEMPLATE_MESSAGE_MAP** (macro) résout le problème en incorporant le paramètre de modèle dans la carte de macro développée. La table des messages pour cette classe est :  
  
 [!code-cpp[NVC_MFC_CListBox#46](../mfc/codesnippet/cpp/how-to-create-a-message-map-for-a-template-class_5.cpp)]  
  
 Ce qui suit illustre l’exemple d’utilisation de la **CSyncListBox** à l’aide de la classe une **CStringList** objet :  
  
 [!code-cpp[NVC_MFC_CListBox#47](../mfc/codesnippet/cpp/how-to-create-a-message-map-for-a-template-class_6.cpp)]  
  
 Pour effectuer le test, le **StringizeElement** fonction doit être spécialisée pour fonctionner avec le **CStringList** classe :  
  
 [!code-cpp[NVC_MFC_CListBox#48](../mfc/codesnippet/cpp/how-to-create-a-message-map-for-a-template-class_7.cpp)]  
  
## <a name="see-also"></a>Voir aussi  
 [BEGIN_TEMPLATE_MESSAGE_MAP](reference/message-map-macros-mfc.md#begin_template_message_map)   
 [Gestion et mappage des messages](../mfc/message-handling-and-mapping.md)

