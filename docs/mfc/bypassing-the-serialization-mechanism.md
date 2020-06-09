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
ms.openlocfilehash: f47cac34f6cdbdae01af98ec28be5af17edf0e25
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84620964"
---
# <a name="bypassing-the-serialization-mechanism"></a>Ignorer le mécanisme de sérialisation

Comme vous l’avez vu, l’infrastructure fournit une méthode par défaut pour lire et écrire des données dans et à partir de fichiers. La sérialisation via un objet archive répond aux besoins d’un grand nombre d’applications. Une telle application lit un fichier entièrement en mémoire, permet à l’utilisateur de mettre à jour le fichier, puis réécrit la version mise à jour sur le disque.

Toutefois, certaines applications s’exécutent sur des données de façon très différente, et pour ces applications, la sérialisation par le biais d’une archive n’est pas appropriée. Les exemples incluent des programmes de base de données, des programmes qui modifient uniquement des parties de fichiers volumineux, des programmes qui écrivent des fichiers texte uniquement et des programmes qui partagent des fichiers de données.

Dans ces cas-là, vous pouvez substituer la fonction [Serialize](reference/cobject-class.md#serialize) d’une manière différente pour effectuer des actions de fichier via un objet [CFile](reference/cfile-class.md) plutôt qu’un objet [CArchive](reference/carchive-class.md) .

Vous pouvez utiliser les `Open` fonctions membres,,, `Read` `Write` `Close` et de la `Seek` classe `CFile` pour ouvrir un fichier, déplacer le pointeur de fichier (Seek) vers un point spécifique dans le fichier, lire un enregistrement (nombre d’octets spécifié) à ce stade, permettre à l’utilisateur de mettre à jour l’enregistrement, puis rechercher à nouveau le même point et réécrire l’enregistrement dans le fichier. L’infrastructure ouvre le fichier pour vous, et vous pouvez utiliser la `GetFile` fonction membre de la classe `CArchive` pour obtenir un pointeur vers l' `CFile` objet. Pour une utilisation encore plus sophistiquée et plus flexible, vous pouvez substituer les fonctions membres [OnOpenDocument](reference/cdocument-class.md#onopendocument) et [OnSaveDocument](reference/cdocument-class.md#onsavedocument) de la classe `CWinApp` . Pour plus d’informations, consultez la classe [CFile](reference/cfile-class.md) dans la *référence MFC*.

Dans ce scénario, votre `Serialize` remplacement ne fait rien, à moins que, par exemple, vous souhaitiez qu’il Lise et écrive un en-tête de fichier pour le maintenir à jour lorsque le document se ferme.

## <a name="see-also"></a>Voir aussi

[Utilisation de documents](using-documents.md)
