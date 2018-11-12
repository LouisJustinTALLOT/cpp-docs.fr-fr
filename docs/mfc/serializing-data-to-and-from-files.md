---
title: Sérialisation des données dans et depuis des fichiers
ms.date: 11/04/2016
helpviewer_keywords:
- documents [MFC], serialization
- documents [MFC], saving
- saving documents
- deserialization [MFC]
- serialization [MFC], role of document
- serialization [MFC], role of data
- data [MFC]
- data [MFC], serializing
- document data [MFC]
ms.assetid: b42a0c68-4bc4-4012-9938-5433a26d2c24
ms.openlocfilehash: 87e216f1959a7c169673822ffa7041ed511817d3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50473617"
---
# <a name="serializing-data-to-and-from-files"></a>Sérialisation des données dans et depuis des fichiers

L'idée de la persistance est qu'un objet doit pouvoir accéder en écriture à son état actuel, indiquée par les valeurs de variables de ses membres, dans un stockage permanent. Par la suite, l'objet peut être recréé en lisant, ou en "désérialisant", l'état de l'objet à partir du stockage persistant. Un point important est que l'objet lui-même doit lire et écrire son propre état. Par conséquent, pour qu'une classe soit permanente, elle doit implémenter les opérations de sérialisation de base.

Le framework fournit une implémentation par défaut pour sauvegarder des documents sur le disque en réponse aux commandes Enregistrer et Enregistrer Sous du menu Fichier et pour charger des documents depuis les fichiers de disque en réponse à la commande Ouvrir. Avec très peu de travail, vous pouvez implémenter la capacité d'un document à écrire et à lire ses données dans et depuis un fichier. La principale chose à faire est de remplacer le [Serialize](../mfc/reference/cobject-class.md#serialize) fonction membre dans votre classe de document.

L’Assistant Application MFC place un remplacement simplifié de la `CDocument` fonction membre `Serialize` dans la classe de document qu’il crée pour vous. Après avoir mis les variables membres de votre application en place, vous pouvez compléter votre substitution `Serialize` avec du code qui envoie les données dans un "objet archive" connecté à un fichier. Un [CArchive](../mfc/reference/carchive-class.md) objet est similaire à la **cin** et **cout** d’entrée/sortie des objets à partir de la bibliothèque iostream C++. Toutefois, `CArchive` lit et écrit le format binaire, pas le texte mis en forme.

## <a name="what-do-you-want-to-know-more-about"></a>Ce que vous souhaitez en savoir plus sur

- [Sérialisation](../mfc/serialization-in-mfc.md)

- [Le rôle du document dans la sérialisation](#_core_the_document.92.s_role_in_serialization)

- [Le rôle des données dans la sérialisation](#_core_the_data.92.s_role_in_serialization)

- [Ignorer le mécanisme de sérialisation](../mfc/bypassing-the-serialization-mechanism.md)

##  <a name="_core_the_document.92.s_role_in_serialization"></a> Le rôle du Document dans la sérialisation

Le framework répond automatiquement aux commandes Ouvrir, Enregistrer et Enregistrer sous du menu Fichier en appelant la fonction membre `Serialize` du document si elle est implémentée. Une commande ID_FILE_OPEN, appelle, par exemple, une fonction de gestionnaire dans l’objet d’application. Au cours de ce processus, l'utilisateur visualise et répond à la boîte de dialogue Fichier - Ouvrir et le framework obtient le nom de fichier que l'utilisateur choisit. Le framework crée l'installation d'un objet `CArchive` pour charger des données dans le document et passe l'archive à `Serialize`. Le framework a déjà ouvert le fichier. Le code de la fonction membre `Serialize` de votre document lit les données à travers l'archive, reconstruisant les objets de données si nécessaire. Pour plus d’informations sur la sérialisation, consultez l’article [sérialisation](../mfc/serialization-in-mfc.md).

##  <a name="_core_the_data.92.s_role_in_serialization"></a> Le rôle des données dans la sérialisation

En général les données de types de classe doivent se sérialiser elles-mêmes. Autrement dit, lorsque vous passez un objet à une archive, l'objet doit savoir comment s'écrire dans l'archive et comment se lire depuis l'archive. MFC fournit une aide pour vous permettre de sérialiser les classes. Si vous concevez une classe pour définir un type de données et que vous envisagez de sérialiser les données de ce type, concevez la sérialisation.

## <a name="see-also"></a>Voir aussi

[Utilisation de documents](../mfc/using-documents.md)

