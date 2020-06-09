---
title: 'Arrière-plan OLE : implémentation MFC'
ms.date: 11/04/2016
f1_keywords:
- IMarshall
- IMoniker
helpviewer_keywords:
- MFC libraries, implementing
- OLE MFC library implementation
- OLE IMarshal interface
- IMoniker interface, MFC
- IMarshall class [MFC]
- OLE, compound files
- OLE IMoniker interface
- OLE IUnknown
ms.assetid: 2b67016a-d78e-4d60-925f-c28ec8fb6180
ms.openlocfilehash: 1dffdafbd02697db5aec341fec253c84217a0faf
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84619872"
---
# <a name="ole-background-mfc-implementation"></a>Arrière-plan OLE : implémentation MFC

En raison de la taille et de la complexité de l'API OLE brute, l'appeler directement pour écrire des applications OLE peut prendre beaucoup de temps. L’objectif de l’implémentation de la bibliothèque MFC OLE est de réduire la charge de travail dans l’écriture des applications complètes et de type OLE.

Cet article explique les parties de l'API OLE qui n'ont pas été implémentées dans MFC. La discussion explique également comment ce qui est implémenté est mappé à la section OLE de l’SDK Windows.

## <a name="portions-of-ole-not-implemented-by-the-class-library"></a><a name="_core_portions_of_ole_not_implemented_by_the_class_library"></a>Parties d’OLE non implémentées par la bibliothèque de classes

Certaines fonctionnalités et interfaces OLE ne sont pas directement fournies par MFC. Si vous souhaitez utiliser ces fonctionnalités, vous pouvez appeler l’API OLE directement.

Interface IMoniker l' `IMoniker` interface est implémentée par la bibliothèque de classes (par exemple, la `COleServerItem` classe), mais elle n’a pas été exposée précédemment au programmeur. Pour plus d’informations sur cette interface, consultez implémentations du moniker OLE dans la section OLE de l’SDK Windows. Toutefois, consultez également la classe [CMonikerFile](reference/cmonikerfile-class.md) et [CAsyncMonikerFile](reference/casyncmonikerfile-class.md).

Interfaces IUnknown et IMarshal l' `IUnknown` interface est implémentée par la bibliothèque de classes, mais n’est pas exposée au programmeur. L' `IMarshal` interface n’est pas implémentée par la bibliothèque de classes, mais est utilisée en interne. Les serveurs d’automation générés à l’aide de la bibliothèque de classes incorporent déjà des fonctions de marshaling.

Les fichiers composés DocFiles (fichiers composés) sont partiellement pris en charge par la bibliothèque de classes. Aucune des fonctions qui manipulent directement les fichiers composés au delà de la création n'est prise en charge. MFC utilise la classe `COleFileStream` pour prendre en charge la manipulation de flux avec des fonctions de fichier standard. Pour plus d’informations, consultez l’article [conteneurs : fichiers composés](containers-compound-files.md).

Les serveurs in-process et les gestionnaires d’objets in-process Servers et les gestionnaires d’objets permettent d’implémenter des données d’édition visuelle ou des objets COM (Component Object Model) complets dans une bibliothèque de liens dynamiques (DLL). Pour cela, vous pouvez implémenter la DLL en appelant l'API OLE directement. Toutefois, si vous disposez d'un accès en écriture à un serveur Automation et que celui-ci n'offre pas d'interface utilisateur, vous pouvez utiliser AppWizard pour faire de votre serveur un serveur intra-processus et l'intégrer complètement dans une DLL. Pour plus d’informations sur ces rubriques, consultez [Serveurs Automation](automation-servers.md).

> [!TIP]
> La façon la plus simple d'implémenter un serveur Automation est de le placer dans une DLL. MFC prend en charge cette méthode.

Pour plus d’informations sur la façon dont les classes Microsoft Foundation OLE implémentent les interfaces OLE, consultez les notes techniques MFC [38](tn038-mfc-ole-iunknown-implementation.md), [39](tn039-mfc-ole-automation-implementation.md)et [40](tn040-mfc-ole-in-place-resizing-and-zooming.md).

## <a name="see-also"></a>Voir aussi

[Arrière-plan OLE](ole-background.md)<br/>
[Arrière-plan OLE : stratégies d'implémentation](ole-background-implementation-strategies.md)
