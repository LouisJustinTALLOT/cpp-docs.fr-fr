---
title: Threads et classes ODBC
ms.date: 11/04/2016
helpviewer_keywords:
- ODBC classes, and threads
- ODBC, multithreaded applications
- threading [MFC], ODBC support
ms.assetid: 16543926-7331-41a6-ba50-72288f2a61b7
ms.openlocfilehash: 8cb5df605bef31e177e976798f975bb4ca14ced7
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213164"
---
# <a name="odbc-classes-and-threads"></a>Threads et classes ODBC

À partir de MFC 4,2, il existe une prise en charge de multithreads pour les classes ODBC MFC. Notez, toutefois, que MFC ne prend pas en charge le multithreading pour les classes DAO.

La prise en charge du multithreading pour les classes ODBC présente des limitations. Étant donné que ces classes encapsulent l’API ODBC, elles sont limitées à la prise en charge du multithreading des composants sur lesquels elles sont générées. Par exemple, de nombreux pilotes ODBC ne sont pas thread-safe ; par conséquent, les classes ODBC MFC ne sont pas thread-safe si vous les utilisez avec l’un de ces pilotes. Vous devez vérifier si votre pilote spécifique est thread-safe.

Lors de la création d’une application multithread, vous devez être très prudent lors de l’utilisation de plusieurs threads pour manipuler le même objet. Par exemple, l’utilisation du même objet `CRecordset` dans deux threads peut provoquer des problèmes lors de la récupération de données ; une opération d’extraction dans un thread peut remplacer les données extraites dans l’autre thread. Une utilisation plus courante des classes ODBC MFC dans des threads distincts consiste à partager un objet `CDatabase` ouvert entre les threads pour utiliser la même connexion ODBC, avec un objet `CRecordset` distinct dans chaque thread. Notez que vous ne devez pas passer un objet `CDatabase` non ouvert à un objet `CRecordset` dans un autre thread.

> [!NOTE]
>  Si vous devez avoir plusieurs threads qui manipulent le même objet, vous devez implémenter les mécanismes de synchronisation appropriés, tels que les sections critiques. N’oubliez pas que certaines opérations, telles que `Open`, ne sont pas protégées. Vous devez être sûr que ces opérations ne seront pas appelées simultanément à partir de threads distincts.

Pour plus d’informations sur la création d’applications multithread, consultez rubriques sur le [Multithreading](../../parallel/multithreading-support-for-older-code-visual-cpp.md).

## <a name="see-also"></a>Voir aussi

[ODBC (Open Database Connectivity)](../../data/odbc/open-database-connectivity-odbc.md)<br/>
[Programmation de l’accès aux données (MFC/ATL)](../../data/data-access-programming-mfc-atl.md)
