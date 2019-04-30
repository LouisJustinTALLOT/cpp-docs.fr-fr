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
ms.openlocfilehash: cf53c498e61bdf0a233d7638649b30e498e27cc5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62392854"
---
# <a name="files-in-mfc"></a>Fichiers dans MFC

Dans les MFC Microsoft Foundation Class Library (), classe [CFile](../mfc/reference/cfile-class.md) gère les opérations d’e/s de fichier normal. Cette série d’articles explique comment ouvrir et fermer les fichiers ainsi que lire et écrire des données dans ces fichiers. Il aborde également les opérations d’état de fichier. Pour obtenir une description montrant comment utiliser les fonctionnalités de sérialisation basée sur un objet de la bibliothèque MFC en tant qu’un autre moyen de lire et écrire des données dans les fichiers, consultez l’article [sérialisation](../mfc/serialization-in-mfc.md).

> [!NOTE]
>  Lorsque vous utilisez MFC `CDocument` objets, le framework effectue une grande partie du travail de sérialisation pour vous. En particulier, l’infrastructure crée et utilise le `CFile` objet. Vous ne devez écrire du code dans votre substitution de la `Serialize` fonction membre de classe `CDocument`.

Le `CFile` classe fournit une interface pour les opérations de fichier binaire à usage général. Le `CStdioFile` et `CMemFile` classes dérivées de `CFile` et `CSharedFile` classe dérivée de `CMemFile` fournir des services de fichiers plus spécialisées.

Pour plus d’informations sur les alternatives à la gestion de fichiers MFC, consultez [gestion des fichiers](../c-runtime-library/file-handling.md) dans le *Run-Time Library Reference*.

Pour plus d’informations sur dérivée `CFile` des classes, consultez le [graphique hiérarchique MFC](../mfc/hierarchy-chart.md).

## <a name="what-do-you-want-to-do"></a>Tu veux faire quoi

*Utiliser CFile*

- [Ouvrez un fichier avec CFile](../mfc/opening-files.md)

- [Lire et écrire un fichier avec CFile](../mfc/reading-and-writing-files.md)

- [Fermer un fichier avec CFile](../mfc/closing-files.md)

- [État du fichier Access avec CFile](../mfc/accessing-file-status.md)

*Utiliser la sérialisation MFC (persistance de l’objet)*

- [Créer une classe sérialisable](../mfc/serialization-making-a-serializable-class.md)

- [Sérialiser un objet via un objet CArchive](../mfc/serialization-serializing-an-object.md)

- [Créer un objet CArchive](../mfc/two-ways-to-create-a-carchive-object.md)

- [Utilisez CArchive <\< et >> opérateurs](../mfc/using-the-carchive-output-and-input-operators.md)

- [Store et de chargement de CObjects et les objets dérivés de CObject via une archive](../mfc/storing-and-loading-cobjects-via-an-archive.md)

## <a name="see-also"></a>Voir aussi

[Concepts](../mfc/mfc-concepts.md)<br/>
[Rubriques MFC générales](../mfc/general-mfc-topics.md)<br/>
[CArchive, classe](../mfc/reference/carchive-class.md)<br/>
[CObject, classe](../mfc/reference/cobject-class.md)
