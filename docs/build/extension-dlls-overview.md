---
title: 'DLL d’extension : vue d’ensemble'
ms.date: 05/06/2019
helpviewer_keywords:
- AFXDLL library
- MFC DLLs [C++], MFC extension DLLs
- DLLs [C++], extension
- shared DLL versions [C++]
- extension DLLs [C++], about MFC extension DLLs
ms.assetid: eb5e10b7-d615-4bc7-908d-e3e99b7b1d5f
ms.openlocfilehash: ea8e950e28907ea1a4a85c1f39392d5505f08c49
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2019
ms.locfileid: "65221360"
---
# <a name="mfc-extension-dlls-overview"></a>DLL d’extension de MFC : vue d’ensemble

Une DLL d’extension MFC est une DLL qui implémente généralement des classes réutilisables dérivées de classes de bibliothèque MFC (Microsoft Foundation Class) existantes. Les dll d’extension MFC sont créées à l’aide de la version de bibliothèque de liens dynamiques de MFC (également appelée version partagée de MFC). Seuls les exécutables MFC (applications ou DLL MFC régulières) qui sont générés avec la version partagée de MFC peuvent utiliser une DLL d’extension MFC. Avec une DLL d’extension MFC, vous pouvez dériver de nouvelles classes personnalisées à partir de MFC, puis proposer cette version étendue de MFC aux applications qui appellent votre DLL.

Les dll d’extension peuvent également être utilisées pour passer des objets dérivés de MFC entre l’application et la DLL. Les fonctions membres associées à l’objet passé existent dans le module dans lequel l’objet a été créé. Étant donné que ces fonctions sont correctement exportées lors de l’utilisation de la version DLL partagée de MFC, vous pouvez passer librement des pointeurs d’objets dérivés de MFC ou MFC entre une application et les dll d’extension MFC qu’elle charge.

Pour obtenir un exemple de DLL qui répond aux exigences de base d’une DLL d’extension MFC, consultez l’exemple MFC [DLLHUSK](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/advanced/dllhusk). Examinez en particulier les fichiers Testdll1. cpp et Testdll2. cpp.

## <a name="what-do-you-want-to-do"></a>Que voulez-vous faire ?

- [Initialiser une DLL d’extension MFC](run-time-library-behavior.md#initializing-extension-dlls)

## <a name="what-do-you-want-to-know-more-about"></a>Sur quels éléments souhaitez-vous obtenir des informations supplémentaires ?

- [Dll d’extension MFC](extension-dlls.md)

- [Utilisation de DLL d’extension MFC de base de données, OLE et sockets dans des DLL MFC normales](using-database-ole-and-sockets-extension-dlls-in-regular-dlls.md)

- [DLL non-MFC : vue d’ensemble](non-mfc-dlls-overview.md)

- [DLL MFC normales liées de manière statique à MFC](regular-dlls-statically-linked-to-mfc.md)

- [DLL MFC normales liées de manière dynamique à MFC](regular-dlls-dynamically-linked-to-mfc.md)

- [Création d’une DLL MFC](../mfc/reference/mfc-dll-wizard.md)

## <a name="see-also"></a>Voir aussi

[Types de DLL](kinds-of-dlls.md)
