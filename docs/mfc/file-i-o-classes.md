---
title: Classes d’e-S de fichier | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.classes.file
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b11996aadd58b456aa919d4ff888c783b4ba486e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33356184"
---
# <a name="file-io-classes"></a>Classes d'E/S de fichier
Ces classes fournissent une interface pour les fichiers de disque traditionnelles, les fichiers en mémoire, des flux de données Active et Windows sockets. Toutes les classes dérivées de `CFile` peut être utilisé avec un `CArchive` objet pour effectuer la sérialisation.  
  
 Utilisez les classes suivantes, en particulier `CArchive` et `CFile`, si vous écrivez votre propre traitement d’entrée/sortie. Généralement il est inutile de dériver à partir de ces classes. Si vous utilisez l’infrastructure d’application, les implémentations par défaut de la **ouvrir** et **enregistrer** des commandes sur le **fichier** menu gérera d’e/s de fichier (à l’aide de la classe `CArchive`), à condition que vous substituez de votre document `Serialize` afin de fournir des détails sur la façon dont un document sérialise à son contenu. Pour plus d’informations sur les classes de fichiers et de sérialisation, consultez l’article [fichiers dans MFC](../mfc/files-in-mfc.md) et l’article [sérialisation](../mfc/serialization-in-mfc.md).  
  
 [CFile](../mfc/reference/cfile-class.md)  
 Fournit une interface de fichier pour les fichiers de disque binaire.  
  
 [CStdioFile](../mfc/reference/cstdiofile-class.md)  
 Fournit un `CFile` interface pour les fichiers de disque de mise en mémoire tampon de flux de données, généralement en mode texte.  
  
 [CMemFile](../mfc/reference/cmemfile-class.md)  
 Fournit un `CFile` interface pour les fichiers en mémoire.  
  
 [CSharedFile](../mfc/reference/csharedfile-class.md)  
 Fournit un `CFile` interface pour les fichiers de mémoire partagées.  
  
 [COleStreamFile](../mfc/reference/colestreamfile-class.md)  
 Utilise le modèle COM `IStream` interface afin de fournir `CFile` accès aux fichiers composés.  
  
 [CSocketFile](../mfc/reference/csocketfile-class.md)  
 Fournit un `CFile` interface à un Socket Windows.  
  
## <a name="related-classes"></a>Classes associées  
 [CArchive](../mfc/reference/carchive-class.md)  
 Collabore avec un `CFile` objet à mettre en œuvre le stockage persistant pour les objets via la sérialisation (consultez [CObject::Serialize](../mfc/reference/cobject-class.md#serialize)).  
  
 [CArchiveException](../mfc/reference/carchiveexception-class.md)  
 Une exception de l’archive.  
  
 [CFileException](../mfc/reference/cfileexception-class.md)  
 Une exception de fichiers.  
  
 [CFileDialog](../mfc/reference/cfiledialog-class.md)  
 Fournit une boîte de dialogue standard d’ouverture ou de l’enregistrement d’un fichier.  
  
 [CRecentFileList](../mfc/reference/crecentfilelist-class.md)  
 Gère la liste (MRU) des fichiers utilisés récemment.  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble de la classe](../mfc/class-library-overview.md)

