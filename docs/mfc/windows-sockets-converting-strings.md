---
description: 'En savoir plus sur : Windows Sockets : conversion de chaînes'
title: 'Windows Sockets : conversion de chaînes'
ms.date: 11/04/2016
helpviewer_keywords:
- Windows Sockets [MFC], multibyte character string conversion
- sockets [MFC], multibyte character string conversion issues
- string conversion, multibyte character strings
ms.assetid: 9df522b5-6b23-41e0-bb96-e4e623baf141
ms.openlocfilehash: fe8607647192fadc7f0d5d32d7716c222ff9206f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97118626"
---
# <a name="windows-sockets-converting-strings"></a>Windows Sockets : conversion de chaînes

Cet article et deux autres articles similaires décrivent plusieurs problèmes de programmation Windows Sockets. Cet article traite de la conversion de chaînes. Les autres problèmes sont traités dans [Windows Sockets : blocage](../mfc/windows-sockets-blocking.md) et [Windows Sockets : classement des octets](../mfc/windows-sockets-byte-ordering.md).

Si vous utilisez ou dérivez de la classe [CAsyncSocket](../mfc/reference/casyncsocket-class.md), vous devrez gérer ces problèmes vous-même. Si vous utilisez ou dérivez de la classe [CSocket](../mfc/reference/csocket-class.md), MFC les gère pour vous.

## <a name="converting-strings"></a>Conversion de chaînes

Si vous communiquez entre des applications qui utilisent des chaînes stockées dans des formats à caractères larges différents, tels que des jeux de caractères Unicode ou multioctets (MBCS), ou entre l’un d’eux et une application utilisant des chaînes de caractères ANSI, vous devez gérer les conversions vous-même sous `CAsyncSocket` . L' `CArchive` objet utilisé avec un `CSocket` objet gère cette conversion à l’aide des fonctionnalités de la classe [CString](../atl-mfc-shared/reference/cstringt-class.md). Pour plus d’informations, consultez la spécification Windows Sockets, située dans le SDK Windows.

Pour plus d'informations, consultez les pages suivantes :

- [Windows Sockets : utilisation de la classe CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md)

- [Windows Sockets : utilisation de sockets avec des Archives](../mfc/windows-sockets-using-sockets-with-archives.md)

- [Windows Sockets : Présentation](../mfc/windows-sockets-background.md)

- [Windows Sockets : Sockets de flux](../mfc/windows-sockets-stream-sockets.md)

- [Windows Sockets : sockets datagrammes](../mfc/windows-sockets-datagram-sockets.md)

## <a name="see-also"></a>Voir aussi

[Windows Sockets dans MFC](../mfc/windows-sockets-in-mfc.md)
