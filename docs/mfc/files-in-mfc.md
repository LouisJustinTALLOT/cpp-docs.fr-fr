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
ms.openlocfilehash: 8b8859e188e42f4419ca7ee7f683cc31de0c75b3
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84625880"
---
# <a name="files-in-mfc"></a>Fichiers dans MFC

Dans le bibliothèque MFC (Microsoft Foundation Class) (MFC), la classe [CFile](reference/cfile-class.md) gère les opérations d’e/s de fichier normales. Cette famille d’articles explique comment ouvrir et fermer des fichiers, ainsi que lire et écrire des données dans ces fichiers. Il traite également des opérations d’état de fichier. Pour obtenir une description de l’utilisation des fonctionnalités de sérialisation basées sur les objets de MFC comme une autre façon de lire et d’écrire des données dans des fichiers, consultez l’article [sérialisation](serialization-in-mfc.md).

> [!NOTE]
> Lorsque vous utilisez `CDocument` des objets MFC, l’infrastructure effectue une grande partie de la sérialisation. En particulier, l’infrastructure crée et utilise l' `CFile` objet. Il vous suffit d’écrire du code dans votre remplacement de la `Serialize` fonction membre de la classe `CDocument` .

La `CFile` classe fournit une interface pour les opérations de fichier binaire à usage général. Les `CStdioFile` `CMemFile` classes et dérivées de `CFile` et la `CSharedFile` classe dérivée de fournissent des services de `CMemFile` fichiers plus spécialisés.

Pour plus d’informations sur les alternatives à la gestion des fichiers MFC, consultez [gestion des fichiers](../c-runtime-library/file-handling.md) dans la référence de la *bibliothèque Runtime*.

Pour plus d’informations sur `CFile` les classes dérivées, consultez le [graphique hiérarchique MFC](hierarchy-chart.md).

## <a name="what-do-you-want-to-do"></a>Tu veux faire quoi

*Utiliser CFile*

- [Ouvrir un fichier avec CFile](opening-files.md)

- [Lire et écrire un fichier avec CFile](reading-and-writing-files.md)

- [Fermer un fichier avec CFile](closing-files.md)

- [Accéder à l’état du fichier avec CFile](accessing-file-status.md)

*Utiliser la sérialisation MFC (persistance des objets)*

- [Créer une classe sérialisable](serialization-making-a-serializable-class.md)

- [Sérialiser un objet à l’aide d’un objet CArchive](serialization-serializing-an-object.md)

- [Créer un objet CArchive](two-ways-to-create-a-carchive-object.md)

- [Utiliser CArchive <\< and >> opérateurs](using-the-carchive-output-and-input-operators.md)

- [Stocker et charger des objets dérivés de CObjects et CObject via une archive](storing-and-loading-cobjects-via-an-archive.md)

## <a name="see-also"></a>Voir aussi

[Concepts](mfc-concepts.md)<br/>
[Rubriques MFC générales](general-mfc-topics.md)<br/>
[CArchive, classe](reference/carchive-class.md)<br/>
[CObject (classe)](reference/cobject-class.md)
