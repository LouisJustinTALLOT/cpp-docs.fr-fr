---
title: Qu’est un objet CArchive | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- CArchive
dev_langs:
- C++
helpviewer_keywords:
- archive objects [MFC]
- archives [MFC], for serialization
- buffers, serializable objects
- CArchive class [MFC], about CArchive class [MFC]
- buffering, serializable objects
ms.assetid: 843f1825-288d-4d89-a1fa-70e1f92d9b8b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 55b97843a8aeb2599d2bdf34458b362fc5899368
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33383827"
---
# <a name="what-is-a-carchive-object"></a>Qu'est-ce qu'un objet CArchive ?
A `CArchive` objet fournit un mécanisme de mise en mémoire tampon de type sécurisé pour l’écriture et la lecture des objets sérialisables vers ou depuis un `CFile` objet. Généralement les `CFile` objet représente un fichier de disque ; Toutefois, il peut également être un fichier de mémoire (`CSharedFile` objet), peut-être représentant le Presse-papiers.  
  
 Une fonction `CArchive` stocke l’objet (écrit, sérialise) données ou charge (lit, désérialise) données, mais jamais les deux. La durée de vie d’un `CArchive` objet est limité à une seule passe via l’écriture d’objets dans un fichier ou de la lecture des objets à partir d’un fichier. Par conséquent, deux successivement créé `CArchive` objets sont requises pour sérialiser les données dans un fichier, puis les désérialiser à partir du fichier.  
  
 Lorsqu’une archive stocke des objets dans un fichier, l’archive attache le `CRuntimeClass` nom aux objets. Ensuite, lorsqu’une autre archive charge les objets à partir d’un fichier en mémoire, le `CObject`-objets dérivés sont reconstruits dynamiquement selon le `CRuntimeClass` des objets. Un objet donné peut être référencé plusieurs fois, telle qu’elle est écrite dans le fichier par l’archive de stockage. L’archive de chargement, toutefois, sera reconstruire l’objet qu’une seule fois. Les détails sur la façon dont une archive attache `CRuntimeClass` plus d’informations pour les objets et reconstruit, en prenant en compte possible de plusieurs références, sont décrits dans [Technical Note 2](../mfc/tn002-persistent-object-data-format.md).  
  
 Comme les données sont sérialisées dans une archive, l’archive accumule les données jusqu'à ce que sa mémoire tampon est saturée. Puis l’archive écrit sa mémoire tampon dans le `CFile` objet vers lequel pointe le `CArchive` objet. De même, lorsque vous lisez des données à partir d’une archive, il lit les données à partir du fichier à la mémoire tampon, puis à partir de la mémoire tampon vers l’objet désérialisé. Cette mise en mémoire tampon permet de réduire le nombre de fois où qu'un disque dur est physiquement lu, ce qui améliore les performances de votre application.  
  
## <a name="see-also"></a>Voir aussi  
 [Sérialisation : sérialisation d’un objet](../mfc/serialization-serializing-an-object.md)

