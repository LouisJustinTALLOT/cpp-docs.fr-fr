---
title: À l’aide de Documents | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- documents [MFC], C++ applications
- data [MFC], reading
- documents [MFC]
- files [MFC], writing to
- data [MFC], documents
- files [MFC]
- views [MFC], C++ applications
- document/view architecture [MFC], documents
- reading data [MFC], documents and views
- printing [MFC], documents
- writing to files [MFC]
ms.assetid: f390d6d8-d0e1-4497-9b6a-435f7ce0776c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6f039b2e81b52c753a1fb065572d4eac53d55ec9
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46428705"
---
# <a name="using-documents"></a>Utilisation de documents

Collaboration, documents et vues :

- Contenir, gérer et afficher votre propre à l’application [données](../mfc/managing-data-with-document-data-variables.md).

- Fournir une interface constituée de [variables de données de document](../mfc/managing-data-with-document-data-variables.md) pour manipuler les données.

- Participer [écrire et lire des fichiers](../mfc/serializing-data-to-and-from-files.md).

- Participer [impression](../mfc/role-of-the-view-in-printing.md).

- [Gérer](../mfc/handling-commands-in-the-document.md) la plupart des commandes et les messages de votre application.

Le document est particulièrement impliqué dans la gestion des données. Store vos données, en règle générale, dans les variables de membres de classe de document. La vue utilise ces variables pour accéder aux données à afficher et mettre à jour. Mécanisme de sérialisation du document par défaut gère la lecture et l’écriture des données vers et à partir de fichiers. Documents peuvent également gérer les commandes (mais pas les messages Windows autres que WM_COMMAND).

## <a name="what-do-you-want-to-know-more-about"></a>Ce que vous souhaitez en savoir plus sur

- [Dérivation d’une classe de document de CDocument](../mfc/deriving-a-document-class-from-cdocument.md)

- [La gestion des données avec variables de données de document](../mfc/managing-data-with-document-data-variables.md)

- [Sérialisation des données vers et à partir de fichiers](../mfc/serializing-data-to-and-from-files.md)

- [Ignorer le mécanisme de sérialisation](../mfc/bypassing-the-serialization-mechanism.md)

- [Gestion des commandes dans le document](../mfc/handling-commands-in-the-document.md)

- [La fonction membre OnNewDocument](../mfc/reference/cdocument-class.md#onnewdocument)

- [La fonction membre DeleteContents](../mfc/reference/cdocument-class.md#deletecontents)

## <a name="see-also"></a>Voir aussi

[Architecture document/vue](../mfc/document-view-architecture.md)

