---
title: 'Windows Sockets : Conversion de chaînes | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Windows Sockets [MFC], multibyte character string conversion
- sockets [MFC], multibyte character string conversion issues
- string conversion, multibyte character strings
ms.assetid: 9df522b5-6b23-41e0-bb96-e4e623baf141
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: bad57be68ce716cddf2ce44f12e94c545a7bbfd6
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33383758"
---
# <a name="windows-sockets-converting-strings"></a>Windows Sockets : conversion de chaînes
Cet article et deux autres articles similaires décrivent plusieurs problèmes de programmation Windows Sockets. Cet article couvre la conversion de chaînes. Les autres problèmes sont traités dans [Windows Sockets : blocage](../mfc/windows-sockets-blocking.md) et [Windows Sockets : classement des octets](../mfc/windows-sockets-byte-ordering.md).  
  
 Si vous utilisez ou dériver de la classe [CAsyncSocket](../mfc/reference/casyncsocket-class.md), vous devrez gérer ces problèmes vous-même. Si vous utilisez ou dériver de la classe [CSocket](../mfc/reference/csocket-class.md), MFC les gère pour vous.  
  
## <a name="converting-strings"></a>Conversion de chaînes  
 Si vous communiquer entre les applications qui utilisent des chaînes stockées dans différents formats de caractères larges, tels que Unicode ou caractères multioctets (MBCS) de définit, ou entre un de ces et une application à l’aide de chaînes de caractères ANSI, vous devez gérer les conversions vous-même sous `CAsyncSocket`. Le `CArchive` objet utilisé avec un `CSocket` objet gère cette conversion automatiquement via les fonctionnalités de la classe [CString](../atl-mfc-shared/reference/cstringt-class.md). Pour plus d’informations, consultez la spécification Windows Sockets située dans le Kit de développement logiciel Windows.  
  
 Pour plus d'informations, voir :  
  
-   [Windows Sockets : utilisation de la classe CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md)  
  
-   [Windows Sockets : utilisation de sockets avec des archives](../mfc/windows-sockets-using-sockets-with-archives.md)  
  
-   [Windows Sockets : arrière-plan](../mfc/windows-sockets-background.md)  
  
-   [Windows Sockets : sockets flux](../mfc/windows-sockets-stream-sockets.md)  
  
-   [Windows Sockets : sockets datagramme](../mfc/windows-sockets-datagram-sockets.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Windows Sockets dans MFC](../mfc/windows-sockets-in-mfc.md)

