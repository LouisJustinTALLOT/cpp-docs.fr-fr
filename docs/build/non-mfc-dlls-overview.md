---
title: 'DLL non MFC : Présentation'
ms.date: 11/04/2016
helpviewer_keywords:
- non-MFC DLLs [C++]
- DLLs [C++], non-MFC
ms.assetid: 1ed5d1ee-e20c-47d7-801d-87ea26a73842
ms.openlocfilehash: 88afb41205e63a837d7bc134133c3c36eccf5dc1
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69493179"
---
# <a name="non-mfc-dlls-overview"></a>DLL non MFC : Présentation

Une DLL non-MFC est une DLL qui n’utilise pas les MFC en interne, et les fonctions exportées dans la DLL peuvent être appelées par des fichiers exécutables MFC ou non-MFC. Les fonctions sont généralement exportées à partir d’une DLL non-MFC à l’aide de l’interface C standard.

Pour plus d’informations sur les dll non-MFC, consultez [bibliothèques de liens dynamiques](/windows/win32/dlls/dynamic-link-libraries) dans le SDK Windows.

## <a name="what-do-you-want-to-do"></a>Que voulez-vous faire ?

- [Procédure pas à pas : Création et utilisation d’une bibliothèque de liens dynamiques](walkthrough-creating-and-using-a-dynamic-link-library-cpp.md)

- [Exporter à partir d’une DLL](exporting-from-a-dll.md)

- [Lier un exécutable à une DLL](linking-an-executable-to-a-dll.md)

- [Initialiser une DLL](run-time-library-behavior.md#initializing-a-dll)

## <a name="what-do-you-want-to-know-more-about"></a>Sur quels éléments souhaitez-vous obtenir des informations supplémentaires ?

- [DLL MFC normales liées de manière statique aux MFC](regular-dlls-statically-linked-to-mfc.md)

- [DLL MFC normales liées de manière dynamique aux MFC](regular-dlls-dynamically-linked-to-mfc.md)

- [DLL d’extension de MFC : Vue d’ensemble](extension-dlls-overview.md)

## <a name="see-also"></a>Voir aussi

[Genres de DLL](kinds-of-dlls.md)
