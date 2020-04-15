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
ms.openlocfilehash: 25c98c3683a8656bb5188f22d0464d25a4901f49
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364530"
---
# <a name="ole-background-mfc-implementation"></a>Arrière-plan OLE : implémentation MFC

En raison de la taille et de la complexité de l'API OLE brute, l'appeler directement pour écrire des applications OLE peut prendre beaucoup de temps. L’objectif de l’implémentation de la bibliothèque MFC OLE est de réduire la charge de travail dans l’écriture des applications complètes et de type OLE.

Cet article explique les parties de l'API OLE qui n'ont pas été implémentées dans MFC. La discussion explique également comment ce qui est mis en œuvre cartes à la section OLE de la SDK Windows.

## <a name="portions-of-ole-not-implemented-by-the-class-library"></a><a name="_core_portions_of_ole_not_implemented_by_the_class_library"></a>Parties de l’OL non mises en œuvre par la Bibliothèque de classe

Certaines fonctionnalités et interfaces OLE ne sont pas directement fournies par MFC. Si vous souhaitez utiliser ces fonctionnalités, vous pouvez appeler l’API OLE directement.

Interface IMoniker `IMoniker` L’interface est implémentée `COleServerItem` par la bibliothèque de classe (par exemple, la classe) mais n’a pas encore été exposée au programmeur. Pour plus d’informations sur cette interface, voir OLE Moniker Implementations dans la section OLE du SDK Windows. Cependant, voir aussi classe [CMonikerFile](../mfc/reference/cmonikerfile-class.md) et [CAsyncMonikerFile](../mfc/reference/casyncmonikerfile-class.md).

Interfaces IUnknown et IMarshal L’interface `IUnknown` est implémentée par la bibliothèque de la classe mais n’est pas exposée au programmeur. L’interface `IMarshal` n’est pas implémentée par la bibliothèque de classe, mais est utilisée en interne. Les serveurs d’automation générés à l’aide de la bibliothèque de classes incorporent déjà des fonctions de marshaling.

Les fichiers composés Docfiles (Compound Files) sont partiellement pris en charge par la bibliothèque de classe. Aucune des fonctions qui manipulent directement les fichiers composés au delà de la création n'est prise en charge. MFC utilise `COleFileStream` la classe pour prendre en charge la manipulation des flux avec des fonctions de fichier standard. Pour plus d’informations, voir l’article [Containers: Compound Files](../mfc/containers-compound-files.md).

Les serveurs en cours et les gestionnaires d’objets en cours permettent la mise en œuvre de données d’édition visuelle ou d’objets complets du modèle d’objet composant (COM) dans une bibliothèque à liaison dynamique (DLL). Pour cela, vous pouvez implémenter la DLL en appelant l'API OLE directement. Toutefois, si vous disposez d'un accès en écriture à un serveur Automation et que celui-ci n'offre pas d'interface utilisateur, vous pouvez utiliser AppWizard pour faire de votre serveur un serveur intra-processus et l'intégrer complètement dans une DLL. Pour plus d’informations sur ces sujets, voir [Serveurs d’automatisation](../mfc/automation-servers.md).

> [!TIP]
> La façon la plus simple d'implémenter un serveur Automation est de le placer dans une DLL. MFC prend en charge cette méthode.

Pour plus d’informations sur la façon dont les classes OLE de la Fondation Microsoft implémentent les interfaces OLE, voir MFC Technical Notes [38](../mfc/tn038-mfc-ole-iunknown-implementation.md), [39](../mfc/tn039-mfc-ole-automation-implementation.md)et [40](../mfc/tn040-mfc-ole-in-place-resizing-and-zooming.md).

## <a name="see-also"></a>Voir aussi

[Arrière-plan OLE](../mfc/ole-background.md)<br/>
[Arrière-plan OLE : stratégies d'implémentation](../mfc/ole-background-implementation-strategies.md)
