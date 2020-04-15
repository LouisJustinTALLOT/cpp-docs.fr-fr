---
title: Fichiers dans MFC
ms.date: 11/04/2016
helpviewer_keywords:
- serialization [MFC], MFC files
- I/O [MFC], MFC classes
- files [MFC], MFC
- files [MFC], serialization
- binary access, binary file operations in MFC
- file I/O classes [MFC]
- I/O [MFC]
- persistence [MFC]
- MFC, file operations
- files [MFC], manipulating
- binary access [MFC]
ms.assetid: ae25e2c5-2859-4679-ab97-438824e93ce1
ms.openlocfilehash: 3a99c4143bbd27ba765b0289b80be8870a940f63
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365317"
---
# <a name="files-in-mfc"></a>Fichiers dans MFC

Dans la Microsoft Foundation Class Library (MFC), la classe [CFile](../mfc/reference/cfile-class.md) gère les opérations normales de fichier I/O. Cette famille d’articles explique comment ouvrir et fermer des fichiers ainsi que lire et écrire des données à ces fichiers. Il traite également des opérations d’état du fichier. Pour une description de la façon d’utiliser les caractéristiques de sérialisation basées sur l’objet de MFC comme une autre façon de lire et d’écrire des données dans les fichiers, voir l’article [Serialization](../mfc/serialization-in-mfc.md).

> [!NOTE]
> Lorsque vous utilisez `CDocument` des objets MFC, le cadre fait une grande partie du travail de sérialisation pour vous. En particulier, le cadre `CFile` crée et utilise l’objet. Vous n’avez qu’à écrire `Serialize` du code `CDocument`dans votre remplacement de la fonction membre de la classe .

La `CFile` classe fournit une interface pour les opérations de fichiers binaires à usage général. Les `CStdioFile` `CMemFile` classes et `CFile` les `CSharedFile` classes `CMemFile` dérivées et de la classe dérivées de la fourniture de services de fichiers plus spécialisés.

Pour plus d’informations sur les solutions de rechange au traitement des fichiers MFC, voir [Traitement des fichiers](../c-runtime-library/file-handling.md) dans la référence de la bibliothèque *Run-Time*.

Pour plus `CFile` d’informations sur les classes dérivées, consultez le [tableau hiérarchique MFC](../mfc/hierarchy-chart.md).

## <a name="what-do-you-want-to-do"></a>Tu veux faire quoi

*Utiliser CFile*

- [Ouvrez un fichier avec CFile](../mfc/opening-files.md)

- [Lire et écrire un fichier avec CFile](../mfc/reading-and-writing-files.md)

- [Fermez un fichier avec CFile](../mfc/closing-files.md)

- [Accéder à l’état du fichier avec CFile](../mfc/accessing-file-status.md)

*Utiliser la sérialisation MFC (Object Persistence)*

- [Créer une classe sérialisable](../mfc/serialization-making-a-serializable-class.md)

- [Sérialiser un objet via un objet CArchive](../mfc/serialization-serializing-an-object.md)

- [Créer un objet CArchive](../mfc/two-ways-to-create-a-carchive-object.md)

- [Utiliser les opérateurs de \< <et de >> CArchive](../mfc/using-the-carchive-output-and-input-operators.md)

- [Stockez et chargez les objets dérivés de CObject et CObject via une archive](../mfc/storing-and-loading-cobjects-via-an-archive.md)

## <a name="see-also"></a>Voir aussi

[Concepts liés à la](../mfc/mfc-concepts.md)<br/>
[Rubriques MFC générales](../mfc/general-mfc-topics.md)<br/>
[CArchive, classe](../mfc/reference/carchive-class.md)<br/>
[Classe CObject](../mfc/reference/cobject-class.md)
