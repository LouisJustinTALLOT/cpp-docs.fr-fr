---
title: Recommandations pour la gestion des entrées-sorties | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- I/O [MFC], about I/O
- file-based I/O options
- I/O [MFC]
- I/O [MFC], options
- I/O [MFC], file-based options
ms.assetid: d664b175-3b4a-40c3-b14b-39de6b12e419
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5e08ea95c9cfe4bd67c0904cc22e6db19dcfb52e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33355680"
---
# <a name="recommendations-for-handling-inputoutput"></a>Recommandations relatives à la gestion des entrées/sorties
L’utilisation d’E/S basées sur des fichiers dépend de la façon dont vous répondez aux questions dans l’arbre de décision suivant :  
  
 **Les données principales dans votre application résident-elles dans un fichier de disque**  
  
-   Oui, les données principales résident dans un fichier sur disque :  
  
     **L’application lit le fichier entier en mémoire sur le fichier ouvert et réécrire la totalité du fichier sur le disque sur l’enregistrement du fichier**  
  
    -   Oui, c'est le cas par défaut des documents MFC. Utilisez **CDocument** sérialisation.  
  
    -   Non, c’est généralement le cas de la mise à jour basée sur des transactions du fichier. Vous mettez à jour le fichier sur une base par transaction et que vous ne devez pas **CDocument** sérialisation.  
  
-   Non, les données principales ne résident pas dans un fichier sur disque :  
  
     **Les données résident-elles dans une source de données ODBC**  
  
    -   Oui, les données résident dans une source de données ODBC :  
  
         Utilisez la prise en charge des bases de données MFC. L’implémentation MFC standard pour ce cas inclut un `CDatabase` de l’objet, comme indiqué dans l’article [MFC : utilisation de Classes de base de données avec des Documents et vues](../data/mfc-using-database-classes-with-documents-and-views.md). L'application peut également lire et écrire un fichier auxiliaire grâce à l'option "Vue de base de données avec prise en charge des fichiers" de l'Assistant Application. Dans ce cas, vous utilisez la sérialisation pour le fichier auxiliaire.  
  
    -   Non, les données ne résident pas dans une source de données ODBC.  
  
         Exemples pour ce cas : les données résident dans un SGBD non-ODBC ; les données sont lues via un autre mécanisme, par exemple OLE ou DDE.  
  
         Dans ces cas, vous n'utilisez pas la sérialisation, et votre application ne contient pas les éléments de menu Ouvrir et Enregistrer. Vous souhaitez toujours utiliser un **CDocument** en tant que base, tout comme une application ODBC MFC application utilise le document pour stocker `CRecordset` objets. Mais vous n'utilisez pas la sérialisation de document Ouvrir/Enregistrer par défaut de le framework.  
  
 Pour prendre en charge les commandes Ouvrir, Enregistrer et Enregistrer sous du menu Fichier, le framework fournit la sérialisation de document. La sérialisation lit et écrit des données, y compris les objets dérivés de la classe `CObject`, dans le stockage permanent, normalement un fichier sur disque. La sérialisation est facile à utiliser et répond à plusieurs de vos besoins, mais elle peut être inappropriée dans de nombreuses applications d'accès aux données. Les applications d'accès aux données mettent généralement à jour les données pour chaque transaction. Elles mettent à jour les enregistrements concernés par la transaction au lieu de lire et d’écrire un fichier de données entier en une seule fois.  
  
 Pour plus d’informations sur la sérialisation, consultez [sérialisation](../mfc/serialization-in-mfc.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Sérialisation : sérialisation et Base de données d’entrée/sortie](../mfc/serialization-serialization-vs-database-input-output.md)
