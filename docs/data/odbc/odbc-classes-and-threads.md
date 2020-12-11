---
description: 'En savoir plus sur : classes et threads ODBC'
title: Threads et classes ODBC
ms.date: 11/04/2016
helpviewer_keywords:
- ODBC classes, and threads
- ODBC, multithreaded applications
- threading [MFC], ODBC support
ms.assetid: 16543926-7331-41a6-ba50-72288f2a61b7
ms.openlocfilehash: bff5ef5a53543b2e0ffa7888f469ed4ce1e54a37
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97161076"
---
# <a name="odbc-classes-and-threads"></a>Threads et classes ODBC

À partir de MFC 4,2, il existe une prise en charge de multithreads pour les classes ODBC MFC. Notez, toutefois, que MFC ne prend pas en charge le multithreading pour les classes DAO.

La prise en charge du multithreading pour les classes ODBC présente des limitations. Étant donné que ces classes encapsulent l’API ODBC, elles sont limitées à la prise en charge du multithreading des composants sur lesquels elles sont générées. Par exemple, de nombreux pilotes ODBC ne sont pas thread-safe ; par conséquent, les classes ODBC MFC ne sont pas thread-safe si vous les utilisez avec l’un de ces pilotes. Vous devez vérifier si votre pilote spécifique est thread-safe.

Lors de la création d’une application multithread, vous devez être très prudent lors de l’utilisation de plusieurs threads pour manipuler le même objet. Par exemple, l’utilisation du même `CRecordset` objet dans deux threads peut provoquer des problèmes lors de la récupération de données ; une opération d’extraction dans un thread peut remplacer les données extraites dans l’autre thread. Une utilisation plus courante des classes ODBC MFC dans des threads distincts consiste à partager un `CDatabase` objet ouvert entre les threads pour utiliser la même connexion ODBC, avec un `CRecordset` objet distinct dans chaque thread. Notez que vous ne devez pas passer un objet non ouvert `CDatabase` à un `CRecordset` objet dans un autre thread.

> [!NOTE]
> Si vous devez avoir plusieurs threads qui manipulent le même objet, vous devez implémenter les mécanismes de synchronisation appropriés, tels que les sections critiques. N’oubliez pas que certaines opérations, telles que `Open` , ne sont pas protégées. Vous devez être sûr que ces opérations ne seront pas appelées simultanément à partir de threads distincts.

Pour plus d’informations sur la création d’applications multithread, consultez rubriques sur le [Multithreading](../../parallel/multithreading-support-for-older-code-visual-cpp.md).

## <a name="see-also"></a>Voir aussi

[Open Database Connectivity (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)<br/>
[Programmation de l’accès aux données (MFC/ATL)](../../data/data-access-programming-mfc-atl.md)
