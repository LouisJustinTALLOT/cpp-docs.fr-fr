---
title: Threads et classes ODBC
ms.date: 11/04/2016
helpviewer_keywords:
- ODBC classes, and threads
- ODBC, multithreaded applications
- threading [MFC], ODBC support
ms.assetid: 16543926-7331-41a6-ba50-72288f2a61b7
ms.openlocfilehash: 1d470e79ba5a6a73a30743a21da0462a6b89e7da
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50608167"
---
# <a name="odbc-classes-and-threads"></a>Threads et classes ODBC

Depuis la version 4.2 de MFC, il existe une prise en charge le multithreading pour les classes ODBC MFC. Notez, cependant, que MFC ne fournit pas de prise en charge le multithreading pour les classes DAO.

La prise en charge le multithreading pour les classes ODBC présente certaines limitations. Étant donné que ces classes encapsulent l’API ODBC, elles sont limitées à la prise en charge le multithreading des composants sur lesquels elles sont construites. Par exemple, de nombreux pilotes ODBC ne sont pas thread-safe. Par conséquent, les classes ODBC MFC ne sont pas thread-safe si vous les utilisez avec un de ces pilotes. Vous devez vérifier si votre pilote particulier est thread-safe.

Lorsque vous créez une application multithread, vous devez être très prudent dans l’utilisation de plusieurs threads pour manipuler le même objet. Par exemple, en utilisant le même `CRecordset` objet dans deux threads peut entraîner des problèmes lors de la récupération des données ; une opération d’extraction dans un thread peut remplacer les données extraites dans l’autre thread. Une utilisation plus courante des classes ODBC MFC dans des threads distincts consiste à partager une open `CDatabase` objet entre plusieurs threads à utiliser la même connexion ODBC, avec un distinct `CRecordset` objet dans chaque thread. Notez que vous ne devez pas passer un non ouvert `CDatabase` de l’objet à un `CRecordset` objet dans un autre thread.

> [!NOTE]
>  Si vous devez avoir plusieurs threads manipulent le même objet, vous devez implémenter les mécanismes de synchronisation appropriées, telles que les sections critiques. N’oubliez pas que certaines opérations, telles que `Open`, ne sont pas protégées. Vous devez être sûr que ces opérations ne seront pas appelées simultanément à partir de threads distincts.

Pour plus d’informations sur la création d’applications multithread, consultez [rubriques de Multithreading](../../parallel/multithreading-support-for-older-code-visual-cpp.md).

## <a name="see-also"></a>Voir aussi

[ODBC (Open Database Connectivity)](../../data/odbc/open-database-connectivity-odbc.md)<br/>
[Accès aux données de programmation (MFC/ATL)](../../data/data-access-programming-mfc-atl.md)