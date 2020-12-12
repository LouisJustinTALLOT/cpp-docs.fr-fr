---
description: 'En savoir plus sur : exceptions : examen du contenu des exceptions'
title: 'Exceptions : examen du contenu des exceptions'
ms.date: 11/04/2016
helpviewer_keywords:
- exception handling [MFC], MFC
- try-catch exception handling [MFC], MFC function exceptions
- catch blocks, MFC function exceptions
- CException class [MFC], class exceptions
- try-catch exception handling [MFC], exception contents
- throwing exceptions [MFC], exception contents
ms.assetid: dfda4782-b969-4f60-b867-cc204ea7f33a
ms.openlocfilehash: aef28d79bd6cad1d810700015930b14b5fdedddc
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97290620"
---
# <a name="exceptions-examining-exception-contents"></a>Exceptions : examen du contenu des exceptions

Bien que **`catch`** l’argument d’un bloc puisse être de presque n’importe quel type de données, les fonctions MFC lèvent des exceptions de types dérivés de la classe `CException` . Pour intercepter une exception levée par une fonction MFC, vous écrivez un **`catch`** bloc dont l’argument est un pointeur vers un `CException` objet (ou un objet dérivé de `CException` , tel que `CMemoryException` ). En fonction du type exact de l’exception, vous pouvez examiner les données membres de l’objet exception pour recueillir des informations sur la cause spécifique de l’exception.

Par exemple, le `CFileException` type a le `m_cause` membre de données, qui contient un type énuméré qui spécifie la cause de l’exception de fichier. Voici quelques exemples de valeurs de retour possibles `CFileException::fileNotFound` `CFileException::readOnly` : et.

L’exemple suivant montre comment examiner le contenu d’un `CFileException` . D’autres types d’exception peuvent être examinés de la même façon.

[!code-cpp[NVC_MFCExceptions#13](codesnippet/cpp/exceptions-examining-exception-contents_1.cpp)]

Pour plus d’informations, consultez [exceptions : libération d’objets dans les exceptions](exceptions-freeing-objects-in-exceptions.md) et [exceptions : interception et suppression d’exceptions](exceptions-catching-and-deleting-exceptions.md).

## <a name="see-also"></a>Voir aussi

[Gestion des exceptions](exception-handling-in-mfc.md)
