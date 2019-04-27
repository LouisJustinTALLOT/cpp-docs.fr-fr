---
title: Deux manières de créer un objet CArchive
ms.date: 11/04/2016
f1_keywords:
- CArchive
helpviewer_keywords:
- CArchive class [MFC], closing CArchive objects
- CArchive objects [MFC], closing
- I/O [MFC], creating CArchive objects
- serialization [MFC], CArchive class
- CArchive objects [MFC]
- storage [MFC], CArchive class [MFC]
- data storage [MFC], CArchive class
- CArchive class [MFC], constructor
ms.assetid: aefa28ce-b55c-40dc-9e42-5f038030985d
ms.openlocfilehash: 80e3e73840bce53691c3f5fdafb62c60bdb8f832
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62181508"
---
# <a name="two-ways-to-create-a-carchive-object"></a>Deux manières de créer un objet CArchive

Il existe deux manières de créer un objet `CArchive` :

- [Création implicite d’un objet CArchive via l’infrastructure](#_core_implicit_creation_of_a_carchive_object_via_the_framework)

- [Création explicite d’un objet CArchive](#_core_explicit_creation_of_a_carchive_object)

##  <a name="_core_implicit_creation_of_a_carchive_object_via_the_framework"></a> Création implicite d’un objet CArchive via l’infrastructure

Les plus courants et, le plus simple consiste à laisser le framework de créer un `CArchive` objet de votre document pour le compte de l’enregistrer, enregistrer sous et les commandes Ouvrir dans le menu fichier.

Voici ce que fait le framework lorsque l’utilisateur de votre application émet la commande Enregistrer sous dans le menu fichier :

1. Présente le **Enregistrer sous** boîte de dialogue et obtient le nom de fichier à partir de l’utilisateur.

1. Ouvre le fichier nommé par l’utilisateur comme un `CFile` objet.

1. Crée un `CArchive` objet qui pointe vers ce `CFile` objet. Lors de la création du `CArchive` de l’objet, le framework définit le mode de « stocker » (écriture, sérialiser), par opposition à « chargement » (lecture, désérialisation).

1. Appelle le `Serialize` fonction définie dans votre `CDocument`-classe dérivée, en lui passant une référence à la `CArchive` objet.

De votre document `Serialize` fonction puis écrit les données de la `CArchive` de l’objet, comme décrit plus bas. Après le retour à partir de votre `Serialize` (fonction), l’infrastructure détruit le `CArchive` objet, puis le `CFile` objet.

Par conséquent, si vous laissez le framework pour créer le `CArchive` de l’objet de votre document, il vous suffit de faire est implémenter du document `Serialize` fonction qui écrit et lit les vers et à partir de l’archive. Vous devez également implémenter `Serialize` pour toute `CObject`-objets dérivés qui du document `Serialize` fonction sérialise à son tour directement ou indirectement.

##  <a name="_core_explicit_creation_of_a_carchive_object"></a> Création explicite d’un objet CArchive

En plus de sérialiser un document par le biais de l’infrastructure, il existe des autres occasions lorsque vous devrez peut-être un `CArchive` objet. Par exemple, vous souhaiterez peut-être sérialiser des données vers et depuis le Presse-papiers, représenté par un `CSharedFile` objet. Ou bien, vous souhaiterez utiliser une interface utilisateur pour enregistrer un fichier qui est différent de celui proposé par l’infrastructure. Dans ce cas, vous pouvez créer explicitement un `CArchive` objet. Pour cela la même manière que le framework, à l’aide de la procédure suivante.

#### <a name="to-explicitly-create-a-carchive-object"></a>Pour créer explicitement un objet CArchive

1. Construire un `CFile` objet ou un objet dérivé de `CFile`.

1. Passer le `CFile` objet au constructeur pour `CArchive`, comme illustré dans l’exemple suivant :

   [!code-cpp[NVC_MFCSerialization#5](../mfc/codesnippet/cpp/two-ways-to-create-a-carchive-object_1.cpp)]

   Le deuxième argument à la `CArchive` constructeur est une valeur énumérée qui spécifie si l’archive doit être utilisée pour stocker ou de chargement des données vers ou à partir du fichier. Le `Serialize` fonction d’un objet vérifie cet état en appelant le `IsStoring` fonction pour l’objet de l’archive.

Lorsque vous avez terminé de stockage ou le chargement des données vers ou depuis le `CArchive` d’objet, fermez-le. Bien que le `CArchive` (et `CFile`) objets seront ferme automatiquement l’archive (et fichier), il est conseillé de faire explicitement dans la mesure où il facilite la récupération des erreurs. Pour plus d’informations sur la gestion des erreurs, consultez l’article [Exceptions : Interception et suppression d’Exceptions](../mfc/exceptions-catching-and-deleting-exceptions.md).

#### <a name="to-close-the-carchive-object"></a>Pour fermer l’objet CArchive

1. L’exemple suivant illustre comment fermer le `CArchive` objet :

   [!code-cpp[NVC_MFCSerialization#6](../mfc/codesnippet/cpp/two-ways-to-create-a-carchive-object_2.cpp)]

## <a name="see-also"></a>Voir aussi

[Sérialisation : Sérialisation d’un objet](../mfc/serialization-serializing-an-object.md)
