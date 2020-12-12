---
description: 'En savoir plus sur : classes d’e/s de fichier'
title: Classes d’e/s de fichier
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
ms.openlocfilehash: b2a0404864cd63ea3992ebada643b15531bcfc3e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97228012"
---
# <a name="file-io-classes"></a>Classes d'E/S de fichier

Ces classes fournissent une interface aux fichiers de disque traditionnels, aux fichiers en mémoire, aux flux actifs et aux sockets Windows. Toutes les classes dérivées de `CFile` peuvent être utilisées avec un `CArchive` objet pour effectuer la sérialisation.

Utilisez les classes suivantes, en particulier `CArchive` et `CFile` , si vous écrivez votre propre traitement d’entrée/sortie. Normalement, vous n’avez pas besoin de dériver de ces classes. Si vous utilisez l’infrastructure d’application, les implémentations par défaut des commandes **ouvrir** et **Enregistrer** du menu **fichier** gèrent les e/s de fichier (à l’aide de la classe `CArchive` ), à condition que vous substituiez la fonction de votre document `Serialize` pour fournir des détails sur la façon dont un document sérialise son contenu. Pour plus d’informations sur les classes de fichier et la sérialisation, consultez l’article [fichiers dans MFC](files-in-mfc.md) et l’article [sérialisation](serialization-in-mfc.md).

[CFile](reference/cfile-class.md)<br/>
Fournit une interface de fichier aux fichiers de disque binaire.

[CStdioFile](reference/cstdiofile-class.md)<br/>
Fournit une `CFile` interface pour mettre en mémoire tampon des fichiers de disque de flux, généralement en mode texte.

[CMemFile](reference/cmemfile-class.md)<br/>
Fournit une `CFile` interface aux fichiers en mémoire.

[CSharedFile](reference/csharedfile-class.md)<br/>
Fournit une `CFile` interface pour partager des fichiers en mémoire.

[COleStreamFile](reference/colestreamfile-class.md)<br/>
Utilise l' `IStream` interface com pour fournir l' `CFile` accès aux fichiers composés.

[CSocketFile](reference/csocketfile-class.md)<br/>
Fournit une `CFile` interface à un socket Windows.

## <a name="related-classes"></a>Classes connexes

[CArchive](reference/carchive-class.md)<br/>
Fonctionne avec un `CFile` objet pour implémenter un stockage persistant pour les objets via la sérialisation (voir [CObject :: Serialize](reference/cobject-class.md#serialize)).

[CArchiveException](reference/carchiveexception-class.md)<br/>
Une exception d’archive.

[CFileException](reference/cfileexception-class.md)<br/>
Une exception orientée fichier.

[CFileDialog](reference/cfiledialog-class.md)<br/>
Fournit une boîte de dialogue standard pour ouvrir ou enregistrer un fichier.

[CRecentFileList](reference/crecentfilelist-class.md)<br/>
Conserve la liste des derniers fichiers utilisés (MRU).

## <a name="see-also"></a>Voir aussi

[Vue d'ensemble des classes](class-library-overview.md)
