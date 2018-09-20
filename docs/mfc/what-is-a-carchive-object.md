---
title: Qu’est un objet CArchive | Microsoft Docs
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
ms.openlocfilehash: fe45b3e5444549001990f62db7028f9de6d49986
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46409661"
---
# <a name="what-is-a-carchive-object"></a>Qu'est-ce qu'un objet CArchive ?

Un `CArchive` objet fournit un mécanisme de mise en mémoire tampon de type sécurisé pour l’écriture ou la lecture des objets sérialisables vers ou depuis un `CFile` objet. Généralement le `CFile` objet représente un fichier de disque ; Toutefois, il peut également être un fichier de mémoire (`CSharedFile` objet), représentant peut-être le Presse-papiers.

A compte tenu de `CArchive` stocke l’objet (écrit, sérialise) données ou charge (lit, désérialise) les données, mais jamais les deux. La durée de vie d’un `CArchive` objet est limité à une seule passe via l’écriture des objets dans un fichier ou de la lecture des objets à partir d’un fichier. Par conséquent, deux successivement créé `CArchive` objets sont nécessaires pour sérialiser les données dans un fichier et ensuite de le désérialiser à partir du fichier.

En cas d’une archive stocke des objets dans un fichier, l’archive attache le `CRuntimeClass` nom aux objets. Ensuite, quand une autre archive charge les objets d’un fichier vers la mémoire, le `CObject`-objets dérivés sont reconstruits dynamiquement selon le `CRuntimeClass` des objets. Un objet donné peut être référencé plusieurs fois, telle qu’elle est écrite dans le fichier par l’archive de stockage. L’archive de chargement, toutefois, sera reconstruire l’objet d’une seule fois. Les détails sur la façon dont une archive attache `CRuntimeClass` informations pour les objets et reconstruit, en prenant en compte possible de plusieurs références, sont décrits dans [Technical Note 2](../mfc/tn002-persistent-object-data-format.md).

Comme les données sont sérialisées dans une archive, l’archive accumule les données jusqu'à ce que sa mémoire tampon est saturée. Puis l’archive écrit sa mémoire tampon dans le `CFile` objet vers lequel pointe le `CArchive` objet. De même, que vous lire les données à partir d’une archive, il lit les données à partir du fichier à sa mémoire tampon, puis à partir de la mémoire tampon vers l’objet désérialisé. Cette mise en mémoire tampon permet de réduire le nombre de fois où qu'un disque dur lecture physique, ce qui améliore les performances de votre application.

## <a name="see-also"></a>Voir aussi

[Sérialisation : sérialisation d’un objet](../mfc/serialization-serializing-an-object.md)

