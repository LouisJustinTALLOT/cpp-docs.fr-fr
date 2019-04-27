---
title: 'Arrière-plan OLE : Implémentation MFC'
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
ms.openlocfilehash: f793c7d7303a49057e46c32eb658ea7eea8e9ccc
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62186727"
---
# <a name="ole-background-mfc-implementation"></a>Arrière-plan OLE : Implémentation MFC

En raison de la taille et de la complexité de l'API OLE brute, l'appeler directement pour écrire des applications OLE peut prendre beaucoup de temps. L’objectif de l’implémentation de la bibliothèque MFC OLE est de réduire la charge de travail dans l’écriture des applications complètes et de type OLE.

Cet article explique les parties de l'API OLE qui n'ont pas été implémentées dans MFC. La discussion explique également comment ce qui est implémenté mappe à la section OLE du Kit de développement Windows.

##  <a name="_core_portions_of_ole_not_implemented_by_the_class_library"></a> Parties OLE non implémentées par la bibliothèque de classes

Certaines fonctionnalités et interfaces OLE ne sont pas directement fournies par MFC. Si vous souhaitez utiliser ces fonctionnalités, vous pouvez appeler l’API OLE directement.

IMoniker Interface le `IMoniker` interface est implémentée par la bibliothèque de classes (par exemple, le `COleServerItem` classe), mais n’a ne pas été exposée au programmeur précédemment. Pour plus d’informations sur cette interface, consultez les implémentations du Moniker OLE dans la section OLE du Kit de développement Windows. Toutefois, consultez également la classe [CMonikerFile](../mfc/reference/cmonikerfile-class.md) et [CAsyncMonikerFile](../mfc/reference/casyncmonikerfile-class.md).

Interfaces IUnknown et IMarshal le `IUnknown` interface est implémentée par la bibliothèque de classes mais n’est pas exposée au programmeur. Le `IMarshal` interface n’est pas implémentée par la bibliothèque de classes mais est utilisée en interne. Les serveurs d’automation générés à l’aide de la bibliothèque de classes incorporent déjà des fonctions de marshaling.

Docfiles (fichiers composés) les fichiers composés sont partiellement pris en charge par la bibliothèque de classes. Aucune des fonctions qui manipulent directement les fichiers composés au delà de la création n'est prise en charge. MFC utilise la classe `COleFileStream` pour prendre en charge la manipulation des flux avec les fonctions de fichier standard. Pour plus d’informations, consultez l’article [conteneurs : Fichiers composés](../mfc/containers-compound-files.md).

Les serveurs in-Process et gestionnaires d’objets serveurs In-process et gestionnaires d’objets autorisent l’implémentation de données de modification visuelle ou des objets de composant COM (Object Model) dans une bibliothèque de liens dynamiques (DLL). Pour cela, vous pouvez implémenter la DLL en appelant l'API OLE directement. Toutefois, si vous disposez d'un accès en écriture à un serveur Automation et que celui-ci n'offre pas d'interface utilisateur, vous pouvez utiliser AppWizard pour faire de votre serveur un serveur intra-processus et l'intégrer complètement dans une DLL. Pour plus d’informations sur ces sujets, consultez [serveurs Automation](../mfc/automation-servers.md).

> [!TIP]
>  La façon la plus simple d'implémenter un serveur Automation est de le placer dans une DLL. MFC prend en charge cette méthode.

Pour plus d’informations sur la façon dont les classes Microsoft Foundation OLE implémentent les interfaces OLE, consultez les Notes techniques MFC [38](../mfc/tn038-mfc-ole-iunknown-implementation.md), [39](../mfc/tn039-mfc-ole-automation-implementation.md), et [40](../mfc/tn040-mfc-ole-in-place-resizing-and-zooming.md).

## <a name="see-also"></a>Voir aussi

[Arrière-plan OLE](../mfc/ole-background.md)<br/>
[Arrière-plan OLE : Stratégies d’implémentation](../mfc/ole-background-implementation-strategies.md)
