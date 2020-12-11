---
description: 'En savoir plus sur : utilisation de documents'
title: Utilisation de documents
ms.date: 11/04/2016
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
ms.openlocfilehash: 486604733808fb027d6dd0fbf81bb670c85313f8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97154498"
---
# <a name="using-documents"></a>Utilisation de documents

Travailler ensemble, documents et vues :

- Contiennent, gèrent et affichent les [données](../mfc/managing-data-with-document-data-variables.md)spécifiques à votre application.

- Fournissez une interface composée de [variables de données de document](../mfc/managing-data-with-document-data-variables.md) pour manipuler les données.

- Participer à l' [écriture et](../mfc/serializing-data-to-and-from-files.md)à la lecture de fichiers.

- Participer à [l’impression](../mfc/role-of-the-view-in-printing.md).

- [Gérez](../mfc/handling-commands-in-the-document.md) la plupart des commandes et des messages de votre application.

Le document est particulièrement impliqué dans la gestion des données. Stockez vos données, normalement, dans les variables de membre de classe de document. La vue utilise ces variables pour accéder aux données pour l’affichage et la mise à jour. Le mécanisme de sérialisation par défaut du document gère la lecture et l’écriture des données vers et à partir de fichiers. Les documents peuvent également gérer les commandes (mais pas les messages Windows autres que WM_COMMAND).

## <a name="what-do-you-want-to-know-more-about"></a>Que voulez-vous en savoir plus sur

- [Dérivation d'une classe de document de CDocument](../mfc/deriving-a-document-class-from-cdocument.md)

- [Gestion des données avec variables de données de document](../mfc/managing-data-with-document-data-variables.md)

- [Sérialisation des données dans et depuis des fichiers](../mfc/serializing-data-to-and-from-files.md)

- [Ignorer le mécanisme de sérialisation](../mfc/bypassing-the-serialization-mechanism.md)

- [Gestion des commandes dans le document](../mfc/handling-commands-in-the-document.md)

- [Fonction membre OnNewDocument](../mfc/reference/cdocument-class.md#onnewdocument)

- [Fonction membre DeleteContents](../mfc/reference/cdocument-class.md#deletecontents)

## <a name="see-also"></a>Voir aussi

[Architecture document/vue](../mfc/document-view-architecture.md)
