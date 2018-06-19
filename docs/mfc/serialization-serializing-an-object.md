---
title: 'Sérialisation : Sérialisation d’un objet | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- serializing objects [MFC]
- serialization [MFC], objects
- objects [MFC], serializing
ms.assetid: 1db772b1-ad55-4fcf-b133-126cca082510
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3439857f14f4c4fa78aa2df3e3da8e5c8941938d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33379656"
---
# <a name="serialization-serializing-an-object"></a>Sérialisation : sérialisation d'un objet
L’article [sérialisation : définir une classe sérialisable](../mfc/serialization-making-a-serializable-class.md) montre comment rendre une classe sérialisable. Une fois que vous avez une classe sérialisable, vous pouvez sérialiser des objets de cette classe vers et à partir d’un fichier via un [CArchive](../mfc/reference/carchive-class.md) objet. Cet article explique :  
  
-   [Un objet CArchive est](../mfc/what-is-a-carchive-object.md).  
  
-   [Deux façons de créer un objet CArchive](../mfc/two-ways-to-create-a-carchive-object.md).  
  
-   [Comment utiliser CArchive <\< et >> opérateurs](../mfc/using-the-carchive-output-and-input-operators.md).  
  
-   [Le stockage et chargement d’objets CObject via une archive](../mfc/storing-and-loading-cobjects-via-an-archive.md).  
  
 Vous pouvez laisser l’infrastructure de création de l’archive de votre document sérialisable ou de créer explicitement le `CArchive` vous-même de l’objet. Vous pouvez transférer des données entre un fichier et l’objet sérialisable à l’aide de la <\< et >> opérateurs pour `CArchive` ou, dans certains cas, en appelant le `Serialize` fonction d’un `CObject`-classe dérivée.  
  
## <a name="see-also"></a>Voir aussi  
 [Sérialisation](../mfc/serialization-in-mfc.md)

