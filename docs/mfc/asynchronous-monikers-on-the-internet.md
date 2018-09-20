---
title: Monikers asynchrones sur Internet | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- ActiveX controls [MFC], asynchronous
- MFC, asynchronous monikers
- asynchronous monikers [MFC]
- Web applications [MFC], asynchronous
- downloading Internet resources and asynchronous monikers
- optimization [MFC], asynchronous downloading across Internet
- Internet [MFC], asynchronous downloading
ms.assetid: 418b0c64-0046-4dae-8118-c9c762b5822e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: bdb310891cd98e6bf3a8afa0b92cce01e5f5c6ba
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46409897"
---
# <a name="asynchronous-monikers-on-the-internet"></a>Monikers asynchrones sur Internet

Internet nécessite de nouvelles approches pour la conception d'applications en raison de la lenteur de son accès réseau. Les applications doivent réaliser un accès réseau asynchrone pour éviter de bloquer l'interface utilisateur. La classe MFC [CAsyncMonikerFile](../mfc/reference/casyncmonikerfile-class.md) fournit la prise en charge asynchrone pour télécharger des fichiers.

Avec des monikers asynchrones, vous pouvez étendre votre application COM pour télécharger de façon asynchrone depuis Internet et pour fournir un rendu progressif des objets volumineux tels que des images bitmap et des objets VRML. Les monikers asynchrones activent une propriété de contrôle ActiveX ou un fichier sur Internet à télécharger sans bloquer la réponse de l'interface utilisateur.

## <a name="advantages-of-asynchronous-monikers"></a>Avantages des monikers asynchrones

Vous pouvez utiliser les monikers asynchrones pour :

- Télécharger du code et des fichiers sans blocage.

- Télécharger des propriétés dans les contrôles ActiveX sans blocage.

- Recevoir des notifications sur la progression du téléchargement.

- Obtenir des informations sur la progression et l'état de préparation.

- Fournir des informations d'état à l'utilisateur sur la progression.

- Autoriser l'utilisateur à annuler un téléchargement à tout moment.

## <a name="mfc-classes-for-asynchronous-monikers"></a>Classes MFC des monikers asynchrones

[CAsyncMonikerFile](../mfc/reference/casyncmonikerfile-class.md) est dérivée de [CMonikerFile](../mfc/reference/cmonikerfile-class.md), qui, à son tour, est dérivée de [COleStreamFile](../mfc/reference/colestreamfile-class.md). Un objet `COleStreamFile` représente un flux de données ; un objet `CMonikerFile` utilise `IMoniker` pour obtenir les données, et un objet `CAsyncMonikerFile` le fait de façon asynchrone.

Les monikers asynchrones sont utilisés principalement dans les applications Internet et les contrôles ActiveX pour fournir une interface utilisateur réactive pendant les transferts de fichiers. Un parfait exemple de ceci est l’utilisation de [CDataPathProperty](../mfc/reference/cdatapathproperty-class.md) pour fournir des propriétés asynchrones pour les contrôles ActiveX.

## <a name="mfc-classes-for-data-paths-in-activex-controls"></a>Classes MFC pour les chemins de données dans les contrôles ActiveX

Les classes MFC `CDataPathProperty` et [CCachedDataPathProperty](../mfc/reference/ccacheddatapathproperty-class.md) implémentez les propriétés de contrôle ActiveX qui peuvent être chargées de façon asynchrone. Les propriétés asynchrones sont chargées après le lancement synchrone. Les contrôles ActiveX asynchrones appellent à plusieurs reprises un rappel pour indiquer la disponibilité de nouvelles données au cours d'un long processus d'échange de propriétés.

`CDataPathProperty` est dérivé de `CAsyncMonikerFile`. `CCachedDataPathProperty` est dérivé de `CDataPathProperty`. Pour implémenter des propriétés asynchrones dans vos contrôles ActiveX, dérivez une classe de `CDataPathProperty` ou `CCachedDataPathProperty`et remplacer [OnDataAvailable](../mfc/reference/casyncmonikerfile-class.md#ondataavailable) et les autres notifications que vous souhaitez recevoir.

#### <a name="to-download-a-file-using-asynchronous-monikers"></a>Pour télécharger un fichier avec des monikers asynchrones

1. Déclarer une classe dérivée de [CAsyncMonikerFile](../mfc/reference/casyncmonikerfile-class.md).

1. Substituer [OnDataAvailable](../mfc/reference/casyncmonikerfile-class.md#ondataavailable) pour afficher les données.

1. Remplacer les autres fonctions membres, y compris [OnProgress](../mfc/reference/casyncmonikerfile-class.md#onprogress), [OnStartBinding](../mfc/reference/casyncmonikerfile-class.md#onstartbinding), et [OnStopBinding](../mfc/reference/casyncmonikerfile-class.md#onstopbinding).

1. Déclarez une instance de la classe et utilisez-la pour ouvrir des URL.

Pour plus d’informations sur le téléchargement asynchrone dans un contrôle ActiveX, consultez [contrôles ActiveX sur Internet](../mfc/activex-controls-on-the-internet.md).

## <a name="see-also"></a>Voir aussi

[Tâches de programmation Internet MFC](../mfc/mfc-internet-programming-tasks.md)<br/>
[Notions de base de la programmation Internet MFC](../mfc/mfc-internet-programming-basics.md)

