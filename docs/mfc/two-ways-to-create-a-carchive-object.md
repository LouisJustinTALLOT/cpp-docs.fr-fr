---
description: 'En savoir plus sur : deux façons de créer un objet CArchive'
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
ms.openlocfilehash: 21a4321eef2d93cf0b37d157f57e12fa1ba940c8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97263853"
---
# <a name="two-ways-to-create-a-carchive-object"></a>Deux manières de créer un objet CArchive

Il existe deux manières de créer un objet `CArchive` :

- [Création implicite d’un objet CArchive via le Framework](#_core_implicit_creation_of_a_carchive_object_via_the_framework)

- [Création explicite d’un objet CArchive](#_core_explicit_creation_of_a_carchive_object)

## <a name="implicit-creation-of-a-carchive-object-via-the-framework"></a><a name="_core_implicit_creation_of_a_carchive_object_via_the_framework"></a> Création implicite d’un objet CArchive via le Framework

La méthode la plus courante et la plus simple consiste à laisser l’infrastructure créer un `CArchive` objet pour votre document pour le compte des commandes enregistrer, enregistrer sous et ouvrir dans le menu fichier.

Voici ce que fait l’infrastructure lorsque l’utilisateur de votre application émet la commande Enregistrer sous à partir du menu fichier :

1. Affiche la boîte de dialogue **Enregistrer sous** et obtient le nom de fichier de l’utilisateur.

1. Ouvre le fichier nommé par l’utilisateur en tant qu' `CFile` objet.

1. Crée un `CArchive` objet qui pointe vers cet `CFile` objet. Lors de la création de l' `CArchive` objet, l’infrastructure définit le mode sur « Store » (Write, Serialize), par opposition à « Load » (Read, Deserialize).

1. Appelle la `Serialize` fonction définie dans votre `CDocument` classe dérivée de, en lui passant une référence à l' `CArchive` objet.

La fonction de votre document `Serialize` écrit ensuite des données dans l' `CArchive` objet, comme expliqué plus loin. Lors du retour de votre `Serialize` fonction, l’infrastructure détruit l' `CArchive` objet, puis l' `CFile` objet.

Par conséquent, si vous laissez l’infrastructure créer l' `CArchive` objet pour votre document, il vous suffit d’implémenter la fonction du document `Serialize` qui écrit et lit dans l’archive. Vous devez également implémenter `Serialize` pour tous les `CObject` objets dérivés de qui, `Serialize` à son tour, la fonction du document sérialise directement ou indirectement.

## <a name="explicit-creation-of-a-carchive-object"></a><a name="_core_explicit_creation_of_a_carchive_object"></a> Création explicite d’un objet CArchive

Outre la sérialisation d’un document par le biais de l’infrastructure, il est possible que vous ayez besoin d’un `CArchive` objet. Par exemple, vous souhaiterez peut-être sérialiser les données vers et depuis le presse-papiers, représenté par un `CSharedFile` objet. Vous pouvez également utiliser une interface utilisateur pour enregistrer un fichier différent de celui proposé par le Framework. Dans ce cas, vous pouvez créer un objet de manière explicite `CArchive` . Pour ce faire, procédez de la même façon que l’infrastructure, à l’aide de la procédure suivante.

#### <a name="to-explicitly-create-a-carchive-object"></a>Pour créer explicitement un objet CArchive

1. Construisez un `CFile` objet ou un objet dérivé de `CFile` .

1. Transmettez l' `CFile` objet au constructeur pour `CArchive` , comme indiqué dans l’exemple suivant :

   [!code-cpp[NVC_MFCSerialization#5](../mfc/codesnippet/cpp/two-ways-to-create-a-carchive-object_1.cpp)]

   Le deuxième argument du `CArchive` constructeur est une valeur énumérée qui spécifie si l’archive sera utilisée pour le stockage ou le chargement des données vers ou à partir du fichier. La `Serialize` fonction d’un objet vérifie cet État en appelant la `IsStoring` fonction pour l’objet archive.

Lorsque vous avez terminé de stocker ou de charger des données vers ou à partir de l' `CArchive` objet, fermez-le. Bien que les `CArchive` objets (et `CFile` ) ferment automatiquement l’archive (et le fichier), il est conseillé de le faire explicitement, car il facilite la récupération des erreurs. Pour plus d’informations sur la gestion des erreurs, consultez l’article [exceptions : interception et suppression d’exceptions](../mfc/exceptions-catching-and-deleting-exceptions.md).

#### <a name="to-close-the-carchive-object"></a>Pour fermer l’objet CArchive

1. L’exemple suivant montre comment fermer l' `CArchive` objet :

   [!code-cpp[NVC_MFCSerialization#6](../mfc/codesnippet/cpp/two-ways-to-create-a-carchive-object_2.cpp)]

## <a name="see-also"></a>Voir aussi

[Sérialisation : sérialisation d’un objet](../mfc/serialization-serializing-an-object.md)
