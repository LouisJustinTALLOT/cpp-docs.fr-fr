---
title: 'Date et heure : prise en charge SYSTEMTIME | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- SYSTEMTIME
dev_langs:
- C++
helpviewer_keywords:
- system time
- FILETIME structure, with CTime class
- time [C++], formatting
- SYSTEMTIME structure
- dates [C++], MFC
- formatting [C++], time
ms.assetid: 201528e4-2ffa-48fc-af8f-203aa86d942a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2a4628d2db9c454bb689d4eb8316b77986588047
ms.sourcegitcommit: 997e6b7d336cddb388bb6e9e56527725fcaa0624
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/08/2018
ms.locfileid: "48860483"
---
# <a name="date-and-time-systemtime-support"></a>Date et heure : prise en charge SYSTEMTIME

Le [CTime](../atl-mfc-shared/reference/ctime-class.md) classe a des constructeurs qui acceptent les heures système et fichier à partir de Win32. Si vous utilisez des objets `CTime` à cette fin, vous devez modifier leur initialisation en conséquence, comme expliqué dans cet article.

Pour plus d’informations sur la structure SYSTEMTIME, consultez [SYSTEMTIME](../mfc/reference/systemtime-structure1.md). Pour plus d’informations sur la structure FILETIME, consultez [FILETIME](../mfc/reference/filetime-structure.md).

MFC fournit toujours des constructeurs `CTime` qui prennent des arguments de date/heure dans le style MS-DOS mais, depuis MFC version 3.0, la classe `CTime` prend aussi en charge un constructeur qui utilise une structure `SYSTEMTIME` Win32 et un autre constructeur qui utilise une structure `FILETIME` Win32.

Les nouveaux constructeurs `CTime` sont :

- CTime (const SYSTEMTIME & `sysTime`) ;

- CTime (const FILETIME & `fileTime`) ;

Le *fileTime* paramètre est une référence à un Win32 `FILETIME` structure, qui représente l’heure sous la forme d’une valeur 64 bits, un format plus pratique pour le stockage interne à un `SYSTEMTIME` structure et le format utilisé par Win32 pour représentent l’heure de création du fichier.

Si votre code contient un objet `CTime` initialisé avec la date/heure système, vous devez utiliser le constructeur `SYSTEMTIME` de Win32.

Vous aurez probablement n’utilisera pas `CTime` `FILETIME` directement l’initialisation. Si vous utilisez un `CFile` objet pour manipuler un fichier, [CFile::GetStatus](../mfc/reference/cfile-class.md#getstatus) récupère l’horodatage de fichier pour vous via un `CTime` objet initialisé avec un `FILETIME` structure.

## <a name="what-do-you-want-to-know-more-about"></a>Ce que vous souhaitez en savoir plus sur

- [Date générale et la programmation de temps dans MFC](../atl-mfc-shared/date-and-time.md)

- [Prise en charge de l’Automation de date et de programmation](../atl-mfc-shared/date-and-time-automation-support.md)

## <a name="see-also"></a>Voir aussi

[Date et heure](../atl-mfc-shared/date-and-time.md)
