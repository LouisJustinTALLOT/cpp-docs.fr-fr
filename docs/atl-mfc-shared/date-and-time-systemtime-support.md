---
title: 'Date et heure : prise en charge SYSTEMTIME | Documents Microsoft'
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
ms.openlocfilehash: ecbfd517a0fd535a23920ae21d03f1756babc113
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32355398"
---
# <a name="date-and-time-systemtime-support"></a>Date et heure : prise en charge SYSTEMTIME
Le [CTime](../atl-mfc-shared/reference/ctime-class.md) classe a des constructeurs qui acceptent des heures système et de fichier à partir de Win32. Si vous utilisez des objets `CTime` à cette fin, vous devez modifier leur initialisation en conséquence, comme expliqué dans cet article.  
  
 Pour plus d’informations sur la structure SYSTEMTIME, consultez [SYSTEMTIME](../mfc/reference/systemtime-structure1.md). Pour plus d’informations sur la structure FILETIME, consultez [FILETIME](../mfc/reference/filetime-structure.md).  
  
 MFC fournit toujours des constructeurs `CTime` qui prennent des arguments de date/heure dans le style MS-DOS mais, depuis MFC version 3.0, la classe `CTime` prend aussi en charge un constructeur qui utilise une structure `SYSTEMTIME` Win32 et un autre constructeur qui utilise une structure `FILETIME` Win32.  
  
 Les nouveaux constructeurs `CTime` sont :  
  
-   CTime (const SYSTEMTIME & `sysTime`) ;  
  
-   CTime (const FILETIME & `fileTime`) ;  
  
 Le paramètre `fileTime` est une référence à une structure `FILETIME` Win32, qui représente la date/heure comme une valeur sur 64 bits, qui est un format plus pratique pour le stockage interne qu'une structure `SYSTEMTIME` et le format utilisé par Win32 pour représenter la date/heure de création d'un fichier.  
  
 Si votre code contient un objet `CTime` initialisé avec la date/heure système, vous devez utiliser le constructeur `SYSTEMTIME` de Win32.  
  
 Il est probablement n’utilisera pas `CTime` `FILETIME` directement l’initialisation. Si vous utilisez un `CFile` objet pour manipuler un fichier, [CFile::GetStatus](../mfc/reference/cfile-class.md#getstatus) récupère l’horodatage de fichier pour vous via un `CTime` objet initialisé avec un `FILETIME` structure.  
  
## <a name="what-do-you-want-to-know-more-about"></a>Que voulez-vous en savoir plus  
  
-   [Date général et programmation dans MFC](../atl-mfc-shared/date-and-time.md)  
  
-   [Prise en charge de l’Automation de date et de programmation](../atl-mfc-shared/date-and-time-automation-support.md)  
  
-   [Classes à usage général pour la programmation de l’heure et de la date](../atl-mfc-shared/date-and-time-general-purpose-classes.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Date et heure](../atl-mfc-shared/date-and-time.md)

