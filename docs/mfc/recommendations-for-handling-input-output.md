---
title: Recommandations pour la gestion des entrées-sorties
ms.date: 11/04/2016
helpviewer_keywords:
- I/O [MFC], about I/O
- file-based I/O options
- I/O [MFC]
- I/O [MFC], options
- I/O [MFC], file-based options
ms.assetid: d664b175-3b4a-40c3-b14b-39de6b12e419
ms.openlocfilehash: 956a92fd1761f61081afa2eb9c6cb35fe72b46d6
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/17/2020
ms.locfileid: "79446899"
---
# <a name="recommendations-for-handling-inputoutput"></a>Recommandations relatives à la gestion des entrées/sorties

L’utilisation d’E/S basées sur des fichiers dépend de la façon dont vous répondez aux questions dans l’arbre de décision suivant :

**Les données principales de votre application résident-elles dans un fichier de disque**

- Oui, les données principales résident dans un fichier sur disque :

     **L’application lit-t-elle la totalité du fichier en mémoire à l’ouverture du fichier et réécrit le fichier entier sur le disque lors de l’enregistrement du fichier**

   - Oui, c'est le cas par défaut des documents MFC. Utilisez `CDocument` la sérialisation.

   - Non, c'est généralement le cas de la mise à jour basée sur des transactions du fichier. Vous mettez à jour le fichier en fonction de la transaction et vous n’avez pas besoin de `CDocument` sérialisation.

- Non, les données principales ne résident pas dans un fichier sur disque :

     **Les données résident-elles dans une source de données ODBC ?**

   - Oui, les données résident dans une source de données ODBC :

      Utilisez la prise en charge des bases de données MFC. Dans ce cas, l’implémentation MFC standard comprend un objet `CDatabase`, comme indiqué dans l’article [MFC : utilisation de classes de base de données avec des documents et des vues](../data/mfc-using-database-classes-with-documents-and-views.md). L'application peut également lire et écrire un fichier auxiliaire grâce à l'option "Vue de base de données avec prise en charge des fichiers" de l'Assistant Application. Dans ce cas, vous utilisez la sérialisation pour le fichier auxiliaire.

   - Non, les données ne résident pas dans une source de données ODBC.

      Exemples pour ce cas : les données résident dans un SGBD non-ODBC ; les données sont lues via un autre mécanisme, par exemple OLE ou DDE.

      Dans ces cas, vous n'utilisez pas la sérialisation, et votre application ne contient pas les éléments de menu Ouvrir et Enregistrer. Vous souhaiterez peut-être toujours utiliser une `CDocument` comme base d’hébergement, tout comme une application ODBC MFC utilise le document pour stocker des objets `CRecordset`. Mais vous n'utilisez pas la sérialisation de document Ouvrir/Enregistrer par défaut de le framework.

Pour prendre en charge les commandes Ouvrir, Enregistrer et Enregistrer sous du menu Fichier, le framework fournit la sérialisation de document. La sérialisation lit et écrit des données, y compris les objets dérivés de la classe `CObject`, dans le stockage permanent, normalement un fichier sur disque. La sérialisation est facile à utiliser et répond à plusieurs de vos besoins, mais elle peut être inappropriée dans de nombreuses applications d'accès aux données. Les applications d’accès aux données mettent généralement à jour les données pour chaque transaction. Elles mettent à jour les enregistrements concernés par la transaction au lieu de lire et d'écrire un fichier de données entier en une seule fois.

Pour plus d’informations sur la sérialisation, consultez [sérialisation](../mfc/serialization-in-mfc.md).

## <a name="see-also"></a>Voir aussi

[Sérialisation : sérialisation et entrées/sorties de base de données](../mfc/serialization-serialization-vs-database-input-output.md)
