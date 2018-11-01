---
title: "DLL non-MFC : vue d'ensemble"
ms.date: 11/04/2016
helpviewer_keywords:
- non-MFC DLLs [C++]
- DLLs [C++], non-MFC
ms.assetid: 1ed5d1ee-e20c-47d7-801d-87ea26a73842
ms.openlocfilehash: 5646f346ad8ccc62b838962b677b7f1947783ea9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50649784"
---
# <a name="non-mfc-dlls-overview"></a>DLL non-MFC : vue d'ensemble

Une DLL non - MFC est une DLL qui n’utilise pas MFC en interne, et les fonctions exportées dans la DLL peuvent être appelées par les fichiers exécutables MFC ou non-MFC. Les fonctions sont généralement exportées à partir d’une DLL non - MFC à l’aide de l’interface C standard.

Pour plus d’informations sur les DLL non - MFC, consultez [Dynamic-Link Libraries](https://msdn.microsoft.com/library/windows/desktop/ms682589) dans le SDK Windows.

## <a name="what-do-you-want-to-do"></a>Que voulez-vous faire ?

- [Procédure pas à pas : Création et utilisation d’une bibliothèque de liens dynamiques](../build/walkthrough-creating-and-using-a-dynamic-link-library-cpp.md)

- [Exporter à partir d’une DLL](../build/exporting-from-a-dll.md)

- [Lier un exécutable à une DLL](../build/linking-an-executable-to-a-dll.md)

- [Initialiser une DLL](../build/run-time-library-behavior.md#initializing-a-dll)

## <a name="what-do-you-want-to-know-more-about"></a>Sur quels éléments souhaitez-vous obtenir des informations supplémentaires ?

- [DLL MFC normales liées de manière statique aux MFC](../build/regular-dlls-statically-linked-to-mfc.md)

- [DLL MFC normales liées de manière dynamique aux MFC](../build/regular-dlls-dynamically-linked-to-mfc.md)

- [DLL d’extension de MFC : vue d’ensemble](../build/extension-dlls-overview.md)

## <a name="see-also"></a>Voir aussi

[Genres de DLL](../build/kinds-of-dlls.md)