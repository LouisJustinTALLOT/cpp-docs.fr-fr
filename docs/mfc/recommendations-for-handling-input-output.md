---
title: Recommandations pour le traitement de la production d’intrants
ms.date: 11/04/2016
helpviewer_keywords:
- I/O [MFC], about I/O
- file-based I/O options
- I/O [MFC]
- I/O [MFC], options
- I/O [MFC], file-based options
ms.assetid: d664b175-3b4a-40c3-b14b-39de6b12e419
ms.openlocfilehash: c365120a385c440f09f0ee4c0a2fc52afb55834f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371734"
---
# <a name="recommendations-for-handling-inputoutput"></a>Recommandations relatives à la gestion des entrées/sorties

L’utilisation d’E/S basées sur des fichiers dépend de la façon dont vous répondez aux questions dans l’arbre de décision suivant :

**Les données primaires de votre application résident-elles dans un fichier disque**

- Oui, les données principales résident dans un fichier sur disque :

   **Est-ce que l’application lit l’ensemble du fichier en mémoire sur File Open et rédige le fichier entier sur disque sur File Save**

  - Oui, c'est le cas par défaut des documents MFC. Utilisez `CDocument` la sérialisation.

  - Non, c'est généralement le cas de la mise à jour basée sur des transactions du fichier. Vous mettez à jour le fichier sur une `CDocument` base par transaction et n’avez pas besoin de sérialisation.

- Non, les données principales ne résident pas dans un fichier sur disque :

   **Les données résident-elles dans une source de données ODBC**

  - Oui, les données résident dans une source de données ODBC :

      Utilisez la prise en charge des bases de données MFC. La mise en œuvre `CDatabase` standard de MFC pour ce cas inclut un objet, comme discuté dans l’article [MFC: Using Database Classes with Documents and Views](../data/mfc-using-database-classes-with-documents-and-views.md). L'application peut également lire et écrire un fichier auxiliaire grâce à l'option "Vue de base de données avec prise en charge des fichiers" de l'Assistant Application. Dans ce cas, vous utilisez la sérialisation pour le fichier auxiliaire.

  - Non, les données ne résident pas dans une source de données ODBC.

      Exemples pour ce cas : les données résident dans un SGBD non-ODBC ; les données sont lues via un autre mécanisme, par exemple OLE ou DDE.

      Dans ces cas, vous n'utilisez pas la sérialisation, et votre application ne contient pas les éléments de menu Ouvrir et Enregistrer. Vous pouvez toujours utiliser `CDocument` un comme base d’accueil, tout comme une application `CRecordset` MFC ODBC utilise le document pour stocker des objets. Mais vous n'utilisez pas la sérialisation de document Ouvrir/Enregistrer par défaut de le framework.

Pour prendre en charge les commandes Ouvrir, Enregistrer et Enregistrer sous du menu Fichier, le framework fournit la sérialisation de document. La sérialisation lit et écrit des données, y compris les objets dérivés de la classe `CObject`, dans le stockage permanent, normalement un fichier sur disque. La sérialisation est facile à utiliser et répond à plusieurs de vos besoins, mais elle peut être inappropriée dans de nombreuses applications d'accès aux données. Les applications d’accès aux données mettent généralement à jour les données pour chaque transaction. Elles mettent à jour les enregistrements concernés par la transaction au lieu de lire et d'écrire un fichier de données entier en une seule fois.

Pour plus d’informations sur la sérialisation, voir [Serialization](../mfc/serialization-in-mfc.md).

## <a name="see-also"></a>Voir aussi

[Sérialisation : sérialisation et entrées/sorties de base de données](../mfc/serialization-serialization-vs-database-input-output.md)
