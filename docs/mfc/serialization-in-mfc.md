---
title: Sérialisation dans MFC | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- collection classes [MFC], serialization
- bypassing serialization [MFC]
- MFC, serialization
- serialization [MFC], MFC
- serialization [MFC], bypassing
ms.assetid: fb596a18-4522-47e0-96e0-192732d24c12
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ebd11488f0f86123bcf95d210072cc61dcc31c60
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46409231"
---
# <a name="serialization-in-mfc"></a>Sérialisation dans MFC

Cet article décrit le mécanisme de sérialisation fourni dans la bibliothèque MFC (Microsoft Foundation Class Library) pour permettre aux objets de persister entre les exécutions de votre programme.

La sérialisation est un processus qui consiste à écrire ou à lire un objet vers ou depuis un support de stockage persistant, par exemple un fichier sur disque. Elle convient parfaitement dans les situations où il est souhaitable de conserver l'état des données structurées (telles que les classes ou structures C++) pendant ou après l'exécution d'un programme. L'utilisation des objets de sérialisation fournis par MFC garantit une sérialisation standard et cohérente, en évitant à l'utilisateur de devoir effectuer des opérations de fichier manuelles.

MFC intègre la prise en charge de la sérialisation dans la classe `CObject`. Ainsi, toutes les classes dérivées de `CObject` peuvent tirer parti du protocole de sérialisation de `CObject`.

Le principe fondamental de la sérialisation est qu'un objet doit pouvoir écrire son état actuel, généralement indiqué par la valeur de ses variables membres, dans un support de stockage persistant. Par la suite, l'objet peut être recréé en lisant, ou en désérialisant, l'état de l'objet à partir du support de stockage. La sérialisation gère tous les détails des pointeurs d'objet et des références circulaires aux objets utilisés lorsque vous sérialisez un objet. Un point important est que l'objet lui-même doit lire et écrire son propre état. Par conséquent, pour qu'une classe soit sérialisable, elle doit implémenter les opérations de sérialisation de base. Comme indiqué dans le groupe d'articles sur la sérialisation, il est facile d'ajouter cette fonctionnalité à une classe.

MFC utilise un objet de la classe `CArchive` comme intermédiaire entre l'objet à sérialiser et le support de stockage. Cet objet est toujours associé à un objet `CFile`, à partir duquel il obtient les informations nécessaires à la sérialisation, notamment le nom de fichier et si l'opération demandée est une lecture ou une écriture. L'objet qui effectue une opération de sérialisation peut utiliser l'objet `CArchive`, quelle que soit la nature du support de stockage.

Un `CArchive` objet utilise le mode d’insertion surchargés (**<\<**) et d’extraction (**>>**) pour les opérations de lecture et d’écriture, les opérateurs. Pour plus d’informations, consultez [stockage et chargement d’objets CObject via une Archive](../mfc/storing-and-loading-cobjects-via-an-archive.md) dans l’article sérialisation : sérialisation d’un objet.

> [!NOTE]
>  Ne confondez pas la classe `CArchive` avec les classes iostream à usage général, utilisées pour le texte mis en forme uniquement. La classe `CArchive` est destinée aux objets sérialisés au format binaire.

Si vous le souhaitez, vous pouvez ignorer la sérialisation MFC pour créer votre propre mécanisme de stockage persistant de données. Vous devrez remplacer les fonctions membres de classe qui initialisent la sérialisation sur commande de l'utilisateur. Consultez la discussion dans [Note technique 22](../mfc/tn022-standard-commands-implementation.md) des commandes standards ID_FILE_OPEN, ID_FILE_SAVE et ID_FILE_SAVE_AS.

Les articles suivants détaillent les deux principales tâches requises pour la sérialisation :

- [Sérialisation : définir une classe sérialisable](../mfc/serialization-making-a-serializable-class.md)

- [Sérialisation : sérialisation d’un objet](../mfc/serialization-serializing-an-object.md)

L’article [sérialisation : sérialisation et. Base de données d’entrée/sortie](../mfc/serialization-serialization-vs-database-input-output.md) décrit la sérialisation est une technique d’entrée/sortie appropriée dans les applications de base de données.

## <a name="see-also"></a>Voir aussi

[Concepts](../mfc/mfc-concepts.md)<br/>
[Rubriques MFC générales](../mfc/general-mfc-topics.md)<br/>
[CArchive, classe](../mfc/reference/carchive-class.md)<br/>
[CObject, classe](../mfc/reference/cobject-class.md)<br/>
[CDocument, classe](../mfc/reference/cdocument-class.md)<br/>
[CFile, classe](../mfc/reference/cfile-class.md)
