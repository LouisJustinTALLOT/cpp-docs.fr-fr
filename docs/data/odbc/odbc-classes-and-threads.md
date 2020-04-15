---
title: Threads et classes ODBC
ms.date: 11/04/2016
helpviewer_keywords:
- ODBC classes, and threads
- ODBC, multithreaded applications
- threading [MFC], ODBC support
ms.assetid: 16543926-7331-41a6-ba50-72288f2a61b7
ms.openlocfilehash: aaf54a3a1d616cde5742dad45955bd415f612d60
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368686"
---
# <a name="odbc-classes-and-threads"></a>Threads et classes ODBC

À partir du MFC 4.2, il y a un soutien multithlié pour les classes MFC ODBC. Notez toutefois que le MFC ne fournit pas de soutien multithlié pour les classes DAO.

Le soutien multithlié pour les classes ODBC a quelques limites. Étant donné que ces classes enveloppent l’API ODBC, elles sont limitées au support multithlié des composants sur lesquels ils sont construits. Par exemple, de nombreux conducteurs d’ODBC ne sont pas sans fil; par conséquent, les classes MFC ODBC ne sont pas sans fil si vous les utilisez avec l’un de ces pilotes. Vous devez vérifier si votre pilote particulier est sans fil.

Lors de la création d’une application multithreaded, vous devez être très prudent dans l’utilisation de plusieurs threads pour manipuler le même objet. Par exemple, l’utilisation du même `CRecordset` objet en deux threads peut causer des problèmes lors de la récupération des données; une opération d’aller chercher dans un thread pourrait remplacer les données récupérées dans l’autre thread. Une utilisation plus courante des classes MFC ODBC en `CDatabase` threads séparés est de partager un objet ouvert `CRecordset` à travers les fils pour utiliser la même connexion ODBC, avec un objet séparé dans chaque thread. Notez que vous ne devez `CDatabase` pas passer `CRecordset` un objet non ouvert à un objet dans un autre thread.

> [!NOTE]
> Si vous devez avoir plusieurs threads manipuler le même objet, vous devez implémenter les mécanismes de synchronisation appropriés, tels que les sections critiques. Sachez que certaines opérations, comme `Open`, ne sont pas protégées. Vous devez être sûr que ces opérations ne seront pas appelées en même temps que les threads séparés.

Pour plus d’informations sur la création d’applications multithreaded, voir [Sujets multithreading](../../parallel/multithreading-support-for-older-code-visual-cpp.md).

## <a name="see-also"></a>Voir aussi

[Connectivité open Database (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)<br/>
[Programmation d’accès aux données (MFC/ATL)](../../data/data-access-programming-mfc-atl.md)
