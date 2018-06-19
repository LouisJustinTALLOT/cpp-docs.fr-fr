---
title: Threads et Classes ODBC | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- ODBC classes, and threads
- ODBC, multithreaded applications
- threading [MFC], ODBC support
ms.assetid: 16543926-7331-41a6-ba50-72288f2a61b7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: dedd1f03bf14e0513f9f76a1e292b9180e4d60db
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33090586"
---
# <a name="odbc-classes-and-threads"></a>Threads et classes ODBC
Depuis la version 4.2 de MFC, il existe une prise en charge le multithreading pour les classes ODBC MFC. Toutefois, notez que MFC ne fournit pas de prise en charge le multithreading pour les classes DAO.  
  
 La prise en charge le multithreading pour les classes ODBC présente certaines limitations. Étant donné que ces classes encapsulent l’API ODBC, elles sont limitées à la prise en charge de multithreading des composants sur lesquels elles sont construites. Par exemple, de nombreux pilotes ODBC ne sont pas thread-safe ; Par conséquent, les classes ODBC MFC ne sont pas thread-safe si vous les utilisez avec l’un de ces pilotes. Vous devez vérifier si votre pilote particulier est thread-safe.  
  
 Lorsque vous créez une application multithread, vous devez être très prudent dans l’utilisation de plusieurs threads pour manipuler le même objet. Par exemple, en utilisant le même `CRecordset` objet dans deux threads peut provoquer des problèmes lors de la récupération des données ; une opération d’extraction dans un thread peut remplacer les données extraites dans l’autre thread. Une utilisation plus courante des classes ODBC MFC dans des threads distincts consiste à partager open `CDatabase` objet entre plusieurs threads à utiliser la même connexion ODBC, avec un distinct `CRecordset` objet dans chaque thread. Notez que vous ne devez pas passer un non ouvert `CDatabase` de l’objet à un `CRecordset` objet dans un autre thread.  
  
> [!NOTE]
>  Si vous devez avoir plusieurs threads manipulent le même objet, vous devez implémenter les mécanismes de synchronisation appropriés, tels que les sections critiques. Sachez que certaines opérations, telles que **ouvrir**, ne sont pas protégés. Vous devez être sûr que ces opérations ne seront pas appelées simultanément à partir de threads distincts.  
  
 Pour plus d’informations sur la création d’applications multithread, consultez [rubriques de Multithreading](../../parallel/multithreading-support-for-older-code-visual-cpp.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Open Database Connectivity (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)   
 [Programmation (MFC/ATL) d’accès aux données](../../data/data-access-programming-mfc-atl.md)