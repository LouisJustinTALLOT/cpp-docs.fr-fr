---
title: Deux manières de créer un objet CArchive
ms.date: 11/04/2016
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
ms.openlocfilehash: 38642906b0973730149ed0de5381519f06d69fe5
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/17/2020
ms.locfileid: "79442029"
---
# <a name="two-ways-to-create-a-carchive-object"></a>Deux manières de créer un objet CArchive

Il existe deux manières de créer un objet `CArchive` :

- [Création implicite d’un objet CArchive via le Framework](#_core_implicit_creation_of_a_carchive_object_via_the_framework)

- [Création explicite d’un objet CArchive](#_core_explicit_creation_of_a_carchive_object)

##  <a name="_core_implicit_creation_of_a_carchive_object_via_the_framework"></a>Création implicite d’un objet CArchive via le Framework

La méthode la plus courante et la plus simple consiste à laisser l’infrastructure créer un objet `CArchive` pour votre document pour le compte des commandes enregistrer, enregistrer sous et ouvrir dans le menu fichier.

Voici ce que fait l’infrastructure lorsque l’utilisateur de votre application émet la commande Enregistrer sous à partir du menu fichier :

1. Affiche la boîte de dialogue **Enregistrer sous** et obtient le nom de fichier de l’utilisateur.

1. Ouvre le fichier nommé par l’utilisateur en tant qu’objet `CFile`.

1. Crée un objet `CArchive` qui pointe vers cet objet `CFile`. Lors de la création de l’objet `CArchive`, l’infrastructure définit le mode sur « Store » (Write, Serialize), par opposition à « Load » (Read, Deserialize).

1. Appelle la fonction `Serialize` définie dans votre classe dérivée de `CDocument`, en lui passant une référence à l’objet `CArchive`.

La fonction `Serialize` de votre document écrit ensuite des données dans l’objet `CArchive`, comme expliqué plus loin. Lors du retour de votre fonction `Serialize`, le Framework détruit l’objet `CArchive`, puis l’objet `CFile`.

Par conséquent, si vous laissez l’infrastructure créer l’objet `CArchive` pour votre document, il vous suffit d’implémenter la fonction de `Serialize` du document qui écrit et lit dans l’archive. Vous devez également implémenter `Serialize` pour tous les objets dérivés de `CObject`que la fonction `Serialize` du document sérialise à son tour directement ou indirectement.

##  <a name="_core_explicit_creation_of_a_carchive_object"></a>Création explicite d’un objet CArchive

Outre la sérialisation d’un document par le biais de l’infrastructure, il peut arriver que vous ayez besoin d’un objet `CArchive`. Par exemple, vous souhaiterez peut-être sérialiser les données vers et depuis le presse-papiers, représenté par un objet `CSharedFile`. Vous pouvez également utiliser une interface utilisateur pour enregistrer un fichier différent de celui proposé par le Framework. Dans ce cas, vous pouvez créer explicitement un objet `CArchive`. Pour ce faire, procédez de la même façon que l’infrastructure, à l’aide de la procédure suivante.

#### <a name="to-explicitly-create-a-carchive-object"></a>Pour créer explicitement un objet CArchive

1. Construisez un objet `CFile` ou un objet dérivé de `CFile`.

1. Transmettez l’objet `CFile` au constructeur pour `CArchive`, comme indiqué dans l’exemple suivant :

   [!code-cpp[NVC_MFCSerialization#5](../mfc/codesnippet/cpp/two-ways-to-create-a-carchive-object_1.cpp)]

   Le deuxième argument du constructeur `CArchive` est une valeur énumérée qui spécifie si l’archive sera utilisée pour le stockage ou le chargement des données vers ou à partir du fichier. La fonction `Serialize` d’un objet vérifie cet État en appelant la fonction `IsStoring` pour l’objet archive.

Lorsque vous avez terminé de stocker ou de charger des données vers ou à partir de l’objet `CArchive`, fermez-le. Bien que les objets `CArchive` (et `CFile`) ferment automatiquement l’archive (et le fichier), il est conseillé de le faire explicitement, car il facilite la récupération des erreurs. Pour plus d’informations sur la gestion des erreurs, consultez l’article [exceptions : interception et suppression d’exceptions](../mfc/exceptions-catching-and-deleting-exceptions.md).

#### <a name="to-close-the-carchive-object"></a>Pour fermer l’objet CArchive

1. L’exemple suivant montre comment fermer l’objet `CArchive` :

   [!code-cpp[NVC_MFCSerialization#6](../mfc/codesnippet/cpp/two-ways-to-create-a-carchive-object_2.cpp)]

## <a name="see-also"></a>Voir aussi

[Sérialisation : sérialisation d’un objet](../mfc/serialization-serializing-an-object.md)
