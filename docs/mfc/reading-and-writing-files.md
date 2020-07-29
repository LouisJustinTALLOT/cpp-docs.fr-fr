---
title: Lecture et écriture de fichiers
ms.date: 11/04/2016
helpviewer_keywords:
- CFile class [MFC], objects
- examples [MFC], reading files
- files [MFC], writing to
- examples [MFC], writing to files
- files [MFC], reading
- MFC, file operations
- CFile class [MFC], reading and writing CFile objects
- reading files
- writing to files [MFC]
ms.assetid: cac0c826-ba56-495f-99b3-ce6336f65763
ms.openlocfilehash: f68fd5c48bce214329437cc13fc39da0c3ca7d2b
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87228581"
---
# <a name="reading-and-writing-files"></a>Lecture et écriture de fichiers

Si vous avez utilisé les fonctions de gestion des fichiers de la bibliothèque Runtime C, les opérations de lecture et d’écriture MFC sont familières. Cet article explique comment lire directement et écrire directement dans un `CFile` objet. Vous pouvez également effectuer des e/s de fichier mises en mémoire tampon avec la classe [CArchive](../mfc/reference/carchive-class.md) .

#### <a name="to-read-from-and-write-to-the-file"></a>Pour lire et écrire dans le fichier

1. Utilisez les `Read` `Write` fonctions membres et pour lire et écrire des données dans le fichier.

     -ou-

1. La `Seek` fonction membre peut également être déplacée vers un offset spécifique dans le fichier.

`Read`prend un pointeur vers une mémoire tampon et le nombre d’octets à lire et retourne le nombre réel d’octets qui ont été lus. Si le nombre d’octets requis n’a pas pu être lu parce que la fin du fichier (EOF) est atteinte, le nombre réel d’octets lus est retourné. Si une erreur de lecture se produit, une exception est levée. `Write`est semblable à `Read` , mais le nombre d’octets écrits n’est pas retourné. Si une erreur d’écriture se produit, y compris l’écriture de tous les octets spécifiés, une exception est levée. Si vous avez un `CFile` objet valide, vous pouvez le lire ou y écrire comme indiqué dans l’exemple suivant :

[!code-cpp[NVC_MFCFiles#2](../atl-mfc-shared/reference/codesnippet/cpp/reading-and-writing-files_1.cpp)]

> [!NOTE]
> Normalement, vous devez effectuer des opérations d’entrée/sortie dans un **`try`** / **`catch`** bloc de gestion des exceptions. Pour plus d’informations, consultez [gestion des exceptions (MFC)](../mfc/exception-handling-in-mfc.md).

## <a name="see-also"></a>Voir aussi

[Fichiers](../mfc/files-in-mfc.md)
