---
title: 'DLL non-MFC : Vue d’ensemble | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- non-MFC DLLs [C++]
- DLLs [C++], non-MFC
ms.assetid: 1ed5d1ee-e20c-47d7-801d-87ea26a73842
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 037f6d7bc80956536a7098ee67275425c41a2f68
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42613217"
---
# <a name="non-mfc-dlls-overview"></a>DLL non-MFC : vue d'ensemble
Une DLL non - MFC est une DLL qui n’utilise pas MFC en interne, et les fonctions exportées dans la DLL peuvent être appelées par les fichiers exécutables MFC ou non-MFC. Les fonctions sont généralement exportées à partir d’une DLL non - MFC à l’aide de l’interface C standard.  
  
 Pour plus d’informations sur les DLL non - MFC, consultez [Dynamic-Link Libraries](http://msdn.microsoft.com/library/windows/desktop/ms682589) dans le SDK Windows.  
  
## <a name="what-do-you-want-to-do"></a>Que voulez-vous faire ?  
  
-   [Procédure pas à pas : Création et utilisation d’une bibliothèque de liens dynamiques](../build/walkthrough-creating-and-using-a-dynamic-link-library-cpp.md)  
  
-   [Exporter à partir d’une DLL](../build/exporting-from-a-dll.md)  
  
-   [Lier un exécutable à une DLL](../build/linking-an-executable-to-a-dll.md)  
  
-   [Initialiser une DLL](../build/run-time-library-behavior.md#initializing-a-dll)  
  
## <a name="what-do-you-want-to-know-more-about"></a>Sur quels éléments souhaitez-vous obtenir des informations supplémentaires ?  
  
-   [DLL MFC normales liées de manière statique aux MFC](../build/regular-dlls-statically-linked-to-mfc.md)  
  
-   [DLL MFC normales liées de manière dynamique aux MFC](../build/regular-dlls-dynamically-linked-to-mfc.md)  
  
-   [DLL d’extension de MFC : vue d’ensemble](../build/extension-dlls-overview.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Genres de DLL](../build/kinds-of-dlls.md)