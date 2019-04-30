---
title: Classes d’e / S de fichier
ms.date: 11/04/2016
f1_keywords:
- vc.classes.file
helpviewer_keywords:
- disk file classes [MFC]
- stdio classes [MFC]
- OLE streams [MFC]
- I/O [MFC], MFC classes
- translated stream classes [MFC]
- file I/O classes [MFC]
- I/O [MFC], classes
- sockets classes [MFC]
- stream classes [MFC]
- memory file classes [MFC]
ms.assetid: 92821c3f-d9e1-47f6-98c9-3b632d86e811
ms.openlocfilehash: 914325ec56f0cae30c7293305496d65f358f2731
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62405805"
---
# <a name="file-io-classes"></a>Classes d'E/S de fichier

Ces classes fournissent une interface pour les fichiers de disque classique, les fichiers d’en mémoire, les flux de données Active et les sockets de Windows. Toutes les classes dérivées de `CFile` peut être utilisé avec un `CArchive` objet pour effectuer la sérialisation.

Utilisez les classes suivantes, en particulier `CArchive` et `CFile`, si vous écrivez votre propre traitement d’entrée/sortie. Vous n’avez normalement pas besoin de dériver à partir de ces classes. Si vous utilisez l’infrastructure d’application, les implémentations par défaut de la **Open** et **enregistrer** commandes sur le **fichier** menu gérera d’e/s de fichier (à l’aide de la classe `CArchive`), à condition que vous substituez de votre document `Serialize` (fonction) pour fournir des détails sur la façon dont un document sérialise à son contenu. Pour plus d’informations sur les classes de fichier et de la sérialisation, consultez l’article [fichiers dans MFC](../mfc/files-in-mfc.md) et l’article [sérialisation](../mfc/serialization-in-mfc.md).

[CFile](../mfc/reference/cfile-class.md)<br/>
Fournit une interface de fichier aux fichiers sur disque binaire.

[CStdioFile](../mfc/reference/cstdiofile-class.md)<br/>
Fournit un `CFile` interface pour les fichiers de disque de mise en mémoire tampon de flux de données, généralement en mode texte.

[CMemFile](../mfc/reference/cmemfile-class.md)<br/>
Fournit un `CFile` interface pour les fichiers en mémoire.

[CSharedFile](../mfc/reference/csharedfile-class.md)<br/>
Fournit un `CFile` interface pour les fichiers partagés en mémoire.

[COleStreamFile](../mfc/reference/colestreamfile-class.md)<br/>
Utilise le modèle COM `IStream` interface pour fournir `CFile` accès aux fichiers composés.

[CSocketFile](../mfc/reference/csocketfile-class.md)<br/>
Fournit un `CFile` interface à un Socket Windows.

## <a name="related-classes"></a>Classes connexes

[CArchive](../mfc/reference/carchive-class.md)<br/>
Collabore avec un `CFile` objet pour implémenter le stockage persistant pour les objets via la sérialisation (consultez [CObject::Serialize](../mfc/reference/cobject-class.md#serialize)).

[CArchiveException](../mfc/reference/carchiveexception-class.md)<br/>
Une exception de l’archive.

[CFileException](../mfc/reference/cfileexception-class.md)<br/>
Une exception orienté fichier.

[CFileDialog](../mfc/reference/cfiledialog-class.md)<br/>
Fournit une boîte de dialogue standard pour ouvrir ou enregistrer un fichier.

[CRecentFileList](../mfc/reference/crecentfilelist-class.md)<br/>
Gère le plus récemment (MRU) liste des fichiers utilisés.

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble de la classe](../mfc/class-library-overview.md)
