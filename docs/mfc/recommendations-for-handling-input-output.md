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
ms.openlocfilehash: 760c213c3af7f9c75374f04e3dfc6b9499eade5c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62218562"
---
# <a name="recommendations-for-handling-inputoutput"></a>Recommandations relatives à la gestion des entrées/sorties

L’utilisation d’E/S basées sur des fichiers dépend de la façon dont vous répondez aux questions dans l’arbre de décision suivant :

**Les données principales dans votre application résident-elles dans un fichier de disque**

- Oui, les données principales résident dans un fichier sur disque :

     **L’application lit le fichier entier en mémoire sur le fichier ouvert et réécrire la totalité du fichier sur le disque sur l’enregistrement du fichier**

   - Oui : C’est le cas de document MFC par défaut. Utilisez `CDocument` sérialisation.

   - non : C’est généralement le cas de mise à jour basée sur les transactions du fichier. Vous mettez à jour le fichier sur une base par transaction et que vous n’avez pas besoin `CDocument` sérialisation.

- Non, les données principales ne résident pas dans un fichier sur disque :

     **Les données résident-elles dans une source de données ODBC**

   - Oui, les données résident dans une source de données ODBC :

         Use MFC's database support. The standard MFC implementation for this case includes a `CDatabase` object, as discussed in the article [MFC: Using Database Classes with Documents and Views](../data/mfc-using-database-classes-with-documents-and-views.md). The application might also read and write an auxiliary file — the purpose of the application wizard "both a database view and file support" option. In this case, you'd use serialization for the auxiliary file.

   - Non, les données ne résident pas dans une source de données ODBC.

         Examples of this case: the data resides in a non-ODBC DBMS; the data is read via some other mechanism, such as OLE or DDE.

         In such cases, you won't use serialization, and your application won't have Open and Save menu items. You might still want to use a `CDocument` as a home base, just as an MFC ODBC application uses the document to store `CRecordset` objects. But you won't use the framework's default File Open/Save document serialization.

Pour prendre en charge les commandes Ouvrir, Enregistrer et Enregistrer sous du menu Fichier, le framework fournit la sérialisation de document. La sérialisation lit et écrit des données, y compris les objets dérivés de la classe `CObject`, dans le stockage permanent, normalement un fichier sur disque. La sérialisation est facile à utiliser et répond à plusieurs de vos besoins, mais elle peut être inappropriée dans de nombreuses applications d'accès aux données. Les applications d’accès aux données mettent généralement à jour les données pour chaque transaction. Elles mettent à jour les enregistrements concernés par la transaction au lieu de lire et d'écrire un fichier de données entier en une seule fois.

Pour plus d’informations sur la sérialisation, consultez [sérialisation](../mfc/serialization-in-mfc.md).

## <a name="see-also"></a>Voir aussi

[Sérialisation : Sérialisation ou Base de données d’entrée/sortie](../mfc/serialization-serialization-vs-database-input-output.md)
