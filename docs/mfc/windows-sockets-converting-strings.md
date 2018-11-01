---
title: 'Windows Sockets : conversion de chaînes'
ms.date: 11/04/2016
helpviewer_keywords:
- Windows Sockets [MFC], multibyte character string conversion
- sockets [MFC], multibyte character string conversion issues
- string conversion, multibyte character strings
ms.assetid: 9df522b5-6b23-41e0-bb96-e4e623baf141
ms.openlocfilehash: 984554c2405bf6b8ae6a522e545bcbba6ebae529
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50543726"
---
# <a name="windows-sockets-converting-strings"></a>Windows Sockets : conversion de chaînes

Cet article et deux autres articles similaires décrivent plusieurs problèmes de programmation Windows Sockets. Cet article aborde la conversion de chaînes. Les autres problèmes sont décrits dans [Windows Sockets : blocage](../mfc/windows-sockets-blocking.md) et [Windows Sockets : classement des octets](../mfc/windows-sockets-byte-ordering.md).

Si vous utilisez ou dériver de la classe [CAsyncSocket](../mfc/reference/casyncsocket-class.md), vous devez gérer ces problèmes vous-même. Si vous utilisez ou dériver de la classe [CSocket](../mfc/reference/csocket-class.md), MFC les gèrera.

## <a name="converting-strings"></a>Conversion de chaînes

Si vous communiquez entre les applications qui utilisent des chaînes stockées dans différents formats de caractères larges, telles que Unicode ou caractères multioctets (MBCS) de définit, ou entre un d’eux et une application à l’aide de chaînes de caractères ANSI, vous devez gérer les conversions vous-même sous `CAsyncSocket`. Le `CArchive` objet utilisé avec un `CSocket` objet gère cette conversion à votre place via les fonctionnalités de classe [CString](../atl-mfc-shared/reference/cstringt-class.md). Pour plus d’informations, consultez la spécification Windows Sockets, située dans le SDK Windows.

Pour plus d'informations, voir :

- [Windows Sockets : utilisation de la classe CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md)

- [Windows Sockets : utilisation de sockets avec des archives](../mfc/windows-sockets-using-sockets-with-archives.md)

- [Windows Sockets : arrière-plan](../mfc/windows-sockets-background.md)

- [Windows Sockets : sockets flux](../mfc/windows-sockets-stream-sockets.md)

- [Windows Sockets : sockets datagramme](../mfc/windows-sockets-datagram-sockets.md)

## <a name="see-also"></a>Voir aussi

[Windows Sockets dans MFC](../mfc/windows-sockets-in-mfc.md)

