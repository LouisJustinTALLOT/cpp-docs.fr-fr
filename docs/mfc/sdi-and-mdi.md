---
description: 'En savoir plus sur les éléments suivants : SDI et MDI'
title: SDI et MDI
ms.date: 11/04/2016
helpviewer_keywords:
- frame windows [MFC], SDI applications
- frame windows [MFC], MDI applications
- MFC, windows
- single document interface (SDI) [MFC], applications
- MDI [MFC], vs. SDI
ms.assetid: bb7239d9-4759-4f63-bfff-44a04b48c067
ms.openlocfilehash: bfa54db04a657507b4b491ada6e8f08d17c2d1c9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97217781"
---
# <a name="sdi-and-mdi"></a>SDI et MDI

MFC facilite l’utilisation de l’interface SDI (single-document interface) et des applications d’interface multidocument (MDI).

Les applications SDI n’autorisent qu’une seule fenêtre frame de document ouverte à la fois. Les applications MDI autorisent l’ouverture de plusieurs fenêtres frame de document dans la même instance d’une application. Une application MDI contient une fenêtre dans laquelle plusieurs fenêtres enfants MDI, qui sont des fenêtres Frame elles-mêmes, peuvent être ouvertes, chacune contenant un document distinct. Dans certaines applications, les fenêtres enfants peuvent être de types différents, tels que les fenêtres de graphique et les fenêtres de feuille de calcul. Dans ce cas, la barre de menus peut changer au fur et à mesure que les fenêtres enfants MDI de différents types sont activées.

> [!NOTE]
> Sous Windows 95 et versions ultérieures, les applications sont communément SDI car le système d’exploitation a adopté une vue « document-centré ».

Pour plus d’informations, consultez [documents, vues et le Framework](../mfc/documents-views-and-the-framework.md).

## <a name="see-also"></a>Voir aussi

[Utilisation des classes pour écrire des applications pour Windows](../mfc/using-the-classes-to-write-applications-for-windows.md)
