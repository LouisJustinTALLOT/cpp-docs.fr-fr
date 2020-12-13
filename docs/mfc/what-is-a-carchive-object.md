---
description: 'En savoir plus sur : qu’est-ce qu’un objet CArchive'
title: Qu'est-ce qu'un objet CArchive ?
ms.date: 11/04/2016
helpviewer_keywords:
- archive objects [MFC]
- archives [MFC], for serialization
- buffers, serializable objects
- CArchive class [MFC], about CArchive class [MFC]
- buffering, serializable objects
ms.assetid: 843f1825-288d-4d89-a1fa-70e1f92d9b8b
ms.openlocfilehash: 7d98200f87f4b428a9450894aca5f8958115d627
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97142790"
---
# <a name="what-is-a-carchive-object"></a>Qu'est-ce qu'un objet CArchive ?

Un `CArchive` objet fournit un mécanisme de mise en mémoire tampon de type sécurisé pour l’écriture ou la lecture d’objets sérialisables vers ou à partir d’un `CFile` objet. En général `CFile` , l’objet représente un fichier disque ; Toutefois, il peut également s’agir d’un fichier de mémoire ( `CSharedFile` objet), éventuellement représentant le presse-papiers.

Un `CArchive` objet donné stocke (écrit, sérialise) des données ou charge (lit, désérialise) les données, mais jamais les deux à la fois. La durée de vie d’un `CArchive` objet est limitée à l’écriture d’objets dans un fichier ou à la lecture d’objets à partir d’un fichier. Par conséquent, deux objets créés successivement `CArchive` sont requis pour sérialiser des données dans un fichier, puis les désérialiser à partir du fichier.

Lorsqu’un archivage stocke des objets dans un fichier, l’archive joint le `CRuntimeClass` nom aux objets. Ensuite, lorsqu’une autre archive charge des objets à partir d’un fichier en mémoire, les `CObject` objets dérivés de sont reconstruits de manière dynamique en fonction du `CRuntimeClass` des objets. Un objet donné peut être référencé plusieurs fois lorsqu’il est écrit dans le fichier par l’archive de stockage. Toutefois, l’archive de chargement ne reconstruit l’objet qu’une seule fois. Les détails sur la façon dont une archive joint les `CRuntimeClass` informations aux objets et reconstruit les objets, en tenant compte de plusieurs références possibles, sont décrits dans [Technical Note 2](../mfc/tn002-persistent-object-data-format.md).

À mesure que les données sont sérialisées dans une archive, l’archive accumule les données jusqu’à ce que la mémoire tampon soit saturée. Ensuite, l’archive écrit sa mémoire tampon dans l' `CFile` objet désigné par l' `CArchive` objet. De même, lorsque vous lisez des données à partir d’une archive, elles lisent les données du fichier dans sa mémoire tampon, puis à partir de la mémoire tampon vers votre objet désérialisé. Cette mise en mémoire tampon réduit le nombre de lectures physiques d’un disque dur, ce qui améliore les performances de votre application.

## <a name="see-also"></a>Voir aussi

[Sérialisation : sérialisation d’un objet](../mfc/serialization-serializing-an-object.md)
