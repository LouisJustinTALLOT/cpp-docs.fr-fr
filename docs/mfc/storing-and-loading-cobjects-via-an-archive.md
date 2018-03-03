---
title: "Stockage et chargement d’objets CObject via une Archive | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CObject
dev_langs:
- C++
helpviewer_keywords:
- CObjects [MFC], loading through archives
- CArchive class [MFC], storing and loading objects
- Serialize method, vs. CArchive operators
- CObject class [MFC], CArchive objects
- CObjects [MFC]
ms.assetid: a829b6dd-bc31-47e0-8108-fbb946722db9
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 987f754ccdf03e5a252feae693a1f7718da1b353
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="storing-and-loading-cobjects-via-an-archive"></a>Stockage et chargement de CObjects via une archive
Stockage et chargement `CObject`via une archive nécessite un examen supplémentaire. Dans certains cas, vous devez appeler la `Serialize` fonction de l’objet, où le `CArchive` objet est un paramètre de la `Serialize` appel, au lieu d’utiliser le  **< \<**  ou  **>>**  opérateur de la `CArchive`. L’élément important à prendre en compte est que le `CArchive`  **>>**  opérateur constructions le `CObject` en mémoire selon `CRuntimeClass` précédemment écrites dans le fichier par l’archive de stockage des informations.  
  
 Par conséquent, si vous utilisez la `CArchive`  **< \<**  et  **>>**  opérateurs, plutôt que d’appeler `Serialize`, varie selon que vous *devez* l’archive de chargement doit reconstruire dynamiquement l’objet selon précédemment stockée `CRuntimeClass` plus d’informations. Utilisez le `Serialize` fonction dans les cas suivants :  
  
-   Lors de la désérialisation de l’objet, vous savez exactement de la classe de l’objet au préalable.  
  
-   Lors de la désérialisation de l’objet, vous disposez déjà de mémoire allouée pour celle-ci.  
  
> [!CAUTION]
>  Si vous chargez l’objet en utilisant la `Serialize` (fonction), vous devez également stocker l’objet en utilisant la `Serialize` (fonction). Ne pas stocker à l’aide de la `CArchive`  **<<**  opérateur et le chargement puis à l’aide la `Serialize` , fonction ou stocker à l’aide de la `Serialize` de fonction, puis son chargement à l’aide de **CArchive >>**opérateur.  
  
 L’exemple suivant illustre les cas :  
  
 [!code-cpp[NVC_MFCSerialization#36](../mfc/codesnippet/cpp/storing-and-loading-cobjects-via-an-archive_1.h)]  
  
 [!code-cpp[NVC_MFCSerialization#37](../mfc/codesnippet/cpp/storing-and-loading-cobjects-via-an-archive_2.cpp)]  
  
 En résumé, si votre classe sérialisable définit incorporé **CObjec**t en tant que membre, vous devez *pas* utiliser le `CArchive`  **< \<**  et  **>>**  opérateurs pour cet objet, mais doivent appeler le `Serialize` de fonction à la place. En outre, si votre classe sérialisable définit un pointeur vers un `CObject` (ou un objet dérivé `CObject`) en tant que membre, mais les constructions de cet autre objet dans son propre constructeur, vous devez également appeler `Serialize`.  
  
## <a name="see-also"></a>Voir aussi  
 [Sérialisation : sérialisation d’un objet](../mfc/serialization-serializing-an-object.md)

