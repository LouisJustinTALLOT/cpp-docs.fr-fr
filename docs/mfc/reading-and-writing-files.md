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
ms.openlocfilehash: 6c4b2b21bbfa19fb73997f8475cfa9a4047dc0ca
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371798"
---
# <a name="reading-and-writing-files"></a>Lecture et écriture de fichiers

Si vous avez utilisé les fonctions de traitement des fichiers de la bibliothèque en temps d’exécution C, les opérations de lecture et d’écriture de MFC vous paraîtront familières. Cet article décrit la lecture directe `CFile` et l’écriture directement à un objet. Vous pouvez également faire le fichier tampon I/O avec la classe [CArchive.](../mfc/reference/carchive-class.md)

#### <a name="to-read-from-and-write-to-the-file"></a>Pour lire et écrire au fichier

1. Utilisez `Read` les `Write` fonctions et les fonctions des membres pour lire et écrire des données dans le fichier.

     -ou-

1. La `Seek` fonction membre est également disponible pour passer à une compensation spécifique dans le fichier.

`Read`prend un pointeur à un tampon et le nombre d’octets à lire et retourne le nombre réel d’octets qui ont été lus. Si le nombre requis d’octets n’a pas pu être lu parce que la fin du fichier (EOF) est atteinte, le nombre réel d’octets lus est retourné. Si une erreur de lecture se produit, une exception est lancée. `Write`est similaire `Read`à , mais le nombre d’octets écrits n’est pas retourné. Si une erreur d’écriture se produit, y compris ne pas écrire tous les octets spécifiés, une exception est lancée. Si vous avez `CFile` un objet valide, vous pouvez le lire ou l’écrire comme indiqué dans l’exemple suivant :

[!code-cpp[NVC_MFCFiles#2](../atl-mfc-shared/reference/codesnippet/cpp/reading-and-writing-files_1.cpp)]

> [!NOTE]
> Vous devez normalement effectuer des opérations d’entrée/sortie dans un bloc de manipulation/**d’exception de capture** **d’essai.** Pour plus d’informations, voir [Exception Handling (MFC)](../mfc/exception-handling-in-mfc.md).

## <a name="see-also"></a>Voir aussi

[Fichiers](../mfc/files-in-mfc.md)
