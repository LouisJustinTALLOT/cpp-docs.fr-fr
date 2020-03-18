---
title: Qu'est-ce qu'un objet CArchive ?
ms.date: 11/04/2016
helpviewer_keywords:
- archive objects [MFC]
- archives [MFC], for serialization
- buffers, serializable objects
- CArchive class [MFC], about CArchive class [MFC]
- buffering, serializable objects
ms.assetid: 843f1825-288d-4d89-a1fa-70e1f92d9b8b
ms.openlocfilehash: 0a78385c81c43a4b0c925bbe89ccd3937873ee8b
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/17/2020
ms.locfileid: "79446021"
---
# <a name="what-is-a-carchive-object"></a>Qu'est-ce qu'un objet CArchive ?

Un objet `CArchive` fournit un mécanisme de mise en mémoire tampon de type sécurisé pour l’écriture ou la lecture d’objets sérialisables vers ou à partir d’un objet `CFile`. En général, l’objet `CFile` représente un fichier disque ; Toutefois, il peut également s’agir d’un fichier de mémoire (objet`CSharedFile`), qui représente peut-être le presse-papiers.

Un objet `CArchive` donné stocke (écrit, sérialise) des données ou charge (lit, désérialise) des données, mais jamais les deux à la fois. La durée de vie d’un objet `CArchive` est limitée à l’écriture d’objets dans un fichier ou à la lecture d’objets à partir d’un fichier. Par conséquent, deux objets `CArchive` créés successivement sont requis pour sérialiser des données dans un fichier, puis le désérialiser à partir du fichier.

Lorsqu’un archivage stocke des objets dans un fichier, l’archive joint le nom de `CRuntimeClass` aux objets. Ensuite, lorsqu’une autre archive charge des objets à partir d’un fichier vers la mémoire, les objets dérivés de `CObject`sont reconstruits dynamiquement en fonction de la `CRuntimeClass` des objets. Un objet donné peut être référencé plusieurs fois lorsqu’il est écrit dans le fichier par l’archive de stockage. Toutefois, l’archive de chargement ne reconstruit l’objet qu’une seule fois. Les détails sur la façon dont une archive joint `CRuntimeClass` informations aux objets et reconstruit les objets, en tenant compte de plusieurs références possibles, sont décrits dans [Technical Note 2](../mfc/tn002-persistent-object-data-format.md).

À mesure que les données sont sérialisées dans une archive, l’archive accumule les données jusqu’à ce que la mémoire tampon soit saturée. Ensuite, l’archive écrit sa mémoire tampon dans l’objet `CFile` vers lequel pointe l’objet `CArchive`. De même, lorsque vous lisez des données à partir d’une archive, elles lisent les données du fichier dans sa mémoire tampon, puis à partir de la mémoire tampon vers votre objet désérialisé. Cette mise en mémoire tampon réduit le nombre de lectures physiques d’un disque dur, ce qui améliore les performances de votre application.

## <a name="see-also"></a>Voir aussi

[Sérialisation : sérialisation d’un objet](../mfc/serialization-serializing-an-object.md)
