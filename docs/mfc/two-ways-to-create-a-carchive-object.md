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
ms.openlocfilehash: 71592584d4ecdd3169ad894861a97fa668c04ee8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370959"
---
# <a name="two-ways-to-create-a-carchive-object"></a>Deux manières de créer un objet CArchive

Il existe deux manières de créer un objet `CArchive` :

- [Création implicite d’un objet CArchive via le cadre](#_core_implicit_creation_of_a_carchive_object_via_the_framework)

- [Création explicite d’un objet CArchive](#_core_explicit_creation_of_a_carchive_object)

## <a name="implicit-creation-of-a-carchive-object-via-the-framework"></a><a name="_core_implicit_creation_of_a_carchive_object_via_the_framework"></a>Création implicite d’un objet carchif par le cadre

La façon la plus courante et la plus `CArchive` simple est de laisser le cadre créer un objet pour votre document pour le compte des commandes Enregistrer, enregistrer et ouvrir sur le menu Fichier.

Voici ce que le cadre fait lorsque l’utilisateur de votre application émet la commande Save As du menu Fichier :

1. Présente la boîte de dialogue **Save As** et obtient le nom de fichier de l’utilisateur.

1. Ouvre le fichier nommé par `CFile` l’utilisateur comme objet.

1. Crée `CArchive` un objet qui `CFile` pointe vers cet objet. En créant `CArchive` l’objet, le cadre définit le mode pour « stocker » (écrire, sérialiser), par opposition à la « charge » (lire, déséialiser).

1. Appelle `Serialize` la fonction `CDocument`définie dans votre classe dérivée, en lui passant une référence à l’objet. `CArchive`

La fonction `Serialize` de votre document `CArchive` écrit ensuite des données à l’objet, comme expliqué sous peu. Au retour `Serialize` de votre fonction, `CArchive` le cadre `CFile` détruit l’objet, puis l’objet.

Ainsi, si vous laissez `CArchive` le cadre créer l’objet pour votre document, `Serialize` tout ce que vous avez à faire est de mettre en œuvre la fonction du document qui écrit et lit à et depuis l’archive. Vous devez également `Serialize` implémenter pour tous `CObject` `Serialize` les objets dérivés que la fonction du document sérialisse à son tour directement ou indirectement.

## <a name="explicit-creation-of-a-carchive-object"></a><a name="_core_explicit_creation_of_a_carchive_object"></a>Création explicite d’un objet carchif

En plus de sérialiser un document via le `CArchive` cadre, il y a d’autres occasions où vous pouvez avoir besoin d’un objet. Par exemple, vous pouvez sérialiser des données à l’intérieur et à partir du Clipboard, représentés par un `CSharedFile` objet. Ou, vous pouvez utiliser une interface utilisateur pour enregistrer un fichier qui est différent de celui offert par le cadre. Dans ce cas, vous `CArchive` pouvez créer explicitement un objet. Vous le faites de la même façon que le cadre, en utilisant la procédure suivante.

#### <a name="to-explicitly-create-a-carchive-object"></a>Créer explicitement un objet CArchive

1. Construire `CFile` un objet ou `CFile`un objet dérivé de .

1. Passer l’objet `CFile` au constructeur `CArchive`pour , comme indiqué dans l’exemple suivant:

   [!code-cpp[NVC_MFCSerialization#5](../mfc/codesnippet/cpp/two-ways-to-create-a-carchive-object_1.cpp)]

   Le deuxième argument `CArchive` pour le constructeur est une valeur énumérée qui précise si l’archive sera utilisée pour stocker ou charger des données à ou à partir du fichier. La `Serialize` fonction d’un objet vérifie `IsStoring` cet état en appelant la fonction pour l’objet d’archives.

Lorsque vous avez fini de stocker `CArchive` ou de charger des données à l’endroit ou à partir de l’objet, fermez-les. Bien `CArchive` que `CFile`les objets (et) fermeront automatiquement l’archive (et le fichier), il est de bonne pratique de le faire explicitement car il rend la récupération des erreurs plus facile. Pour plus d’informations sur le traitement des erreurs, voir l’article [Exceptions: Catching and Deleting Exceptions](../mfc/exceptions-catching-and-deleting-exceptions.md).

#### <a name="to-close-the-carchive-object"></a>Fermer l’objet CArchive

1. L’exemple suivant illustre comment `CArchive` fermer l’objet :

   [!code-cpp[NVC_MFCSerialization#6](../mfc/codesnippet/cpp/two-ways-to-create-a-carchive-object_2.cpp)]

## <a name="see-also"></a>Voir aussi

[Sérialisation : sérialisation d’un objet](../mfc/serialization-serializing-an-object.md)
