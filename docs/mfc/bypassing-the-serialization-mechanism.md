---
title: Ignorer le mécanisme de sérialisation
ms.date: 11/04/2016
helpviewer_keywords:
- archive objects [MFC]
- bypassing serialization
- archives [MFC], serialization
- serialization [MFC], bypassing
- archives [MFC]
- serialization [MFC], role of framework
- serialization [MFC], overriding
ms.assetid: 48d4a279-b51c-4ba5-81cd-ed043312b582
ms.openlocfilehash: 1937098de30884be327c67a698dbb0023be248bb
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57276115"
---
# <a name="bypassing-the-serialization-mechanism"></a>Ignorer le mécanisme de sérialisation

Comme vous l’avez vu, le framework fournit un moyen de la valeur par défaut pour lire et écrire des données vers et à partir de fichiers. La sérialisation via un objet archive le mieux aux besoins de très nombreuses applications. Une telle application lit un fichier entièrement en mémoire, permet à l’utilisateur de mettre à jour le fichier, puis écrit la version mise à jour sur le disque.

Toutefois, certaines applications opèrent sur des données très différemment, et ces applications sérialisation via une archive ne convient pas. Exemples incluent les programmes de base de données, programmes que modifier uniquement les parties de fichiers volumineux, les programmes qui écrivent des fichiers en lecture seule et programmes qui partagent des fichiers de données.

Dans ce cas, vous pouvez remplacer le [Serialize](../mfc/reference/cobject-class.md#serialize) fonction d’une manière différente à servant d’intermédiaire des actions de fichier via un [CFile](../mfc/reference/cfile-class.md) objet au lieu d’un [CArchive](../mfc/reference/carchive-class.md) objet.

Vous pouvez utiliser la `Open`, `Read`, `Write`, `Close`, et `Seek` fonctions membres de classe `CFile` pour ouvrir un fichier, placez le pointeur de fichier (recherche) vers un point spécifique dans le fichier, de lire un enregistrement (un nombre spécifié d’octets ) à ce stade, permettre de mettre à jour l’enregistrement, puis rechercher à nouveau au même point et d’écrire l’enregistrement dans le fichier. L’infrastructure, le fichier s’ouvre pour vous, et vous pouvez utiliser la `GetFile` fonction membre de classe `CArchive` pour obtenir un pointeur vers le `CFile` objet. Pour une utilisation encore plus sophistiquée et flexible, vous pouvez remplacer le [OnOpenDocument](../mfc/reference/cdocument-class.md#onopendocument) et [OnSaveDocument](../mfc/reference/cdocument-class.md#onsavedocument) fonctions membres de classe `CWinApp`. Pour plus d’informations, consultez la classe [CFile](../mfc/reference/cfile-class.md) dans le *référence MFC*.

Dans ce scénario, votre `Serialize` override ne fait rien, sauf si, par exemple, vous l’avez lire et écrire un en-tête de fichier pour maintenir à jour lors de la fermeture du document.

## <a name="see-also"></a>Voir aussi

[Utilisation de documents](../mfc/using-documents.md)
