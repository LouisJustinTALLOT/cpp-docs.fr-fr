---
title: 'Windows Sockets : Conversion de chaînes'
ms.date: 11/04/2016
helpviewer_keywords:
- Windows Sockets [MFC], multibyte character string conversion
- sockets [MFC], multibyte character string conversion issues
- string conversion, multibyte character strings
ms.assetid: 9df522b5-6b23-41e0-bb96-e4e623baf141
ms.openlocfilehash: eaf278fc2689f0afa9ab6ff30f1294c36de5d7ac
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62217389"
---
# <a name="windows-sockets-converting-strings"></a>Windows Sockets : Conversion de chaînes

Cet article et deux autres articles similaires décrivent plusieurs problèmes de programmation Windows Sockets. Cet article aborde la conversion de chaînes. Les autres problèmes sont décrits dans [Windows Sockets : Blocage](../mfc/windows-sockets-blocking.md) et [Windows Sockets : L’ordre des octets](../mfc/windows-sockets-byte-ordering.md).

Si vous utilisez ou dériver de la classe [CAsyncSocket](../mfc/reference/casyncsocket-class.md), vous devez gérer ces problèmes vous-même. Si vous utilisez ou dériver de la classe [CSocket](../mfc/reference/csocket-class.md), MFC les gèrera.

## <a name="converting-strings"></a>Conversion de chaînes

Si vous communiquez entre les applications qui utilisent des chaînes stockées dans différents formats de caractères larges, telles que Unicode ou caractères multioctets (MBCS) de définit, ou entre un d’eux et une application à l’aide de chaînes de caractères ANSI, vous devez gérer les conversions vous-même sous `CAsyncSocket`. Le `CArchive` objet utilisé avec un `CSocket` objet gère cette conversion à votre place via les fonctionnalités de classe [CString](../atl-mfc-shared/reference/cstringt-class.md). Pour plus d’informations, consultez la spécification Windows Sockets, située dans le SDK Windows.

Pour plus d'informations, voir :

- [Windows Sockets : Utilisation de la classe CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md)

- [Windows Sockets : Utilisation de sockets avec des archives](../mfc/windows-sockets-using-sockets-with-archives.md)

- [Windows Sockets : Arrière-plan](../mfc/windows-sockets-background.md)

- [Windows Sockets : Sockets flux](../mfc/windows-sockets-stream-sockets.md)

- [Windows Sockets : Sockets datagramme](../mfc/windows-sockets-datagram-sockets.md)

## <a name="see-also"></a>Voir aussi

[Windows Sockets dans MFC](../mfc/windows-sockets-in-mfc.md)
