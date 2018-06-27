---
title: Deux façons de créer un objet CArchive | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- CArchive
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: cba1596e1dd114dcd46610b824405740a783c21e
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2018
ms.locfileid: "36954791"
---
# <a name="two-ways-to-create-a-carchive-object"></a>Deux manières de créer un objet CArchive
Il existe deux manières de créer un objet `CArchive` :  
  
-   [Création implicite d’un objet CArchive via la structure](#_core_implicit_creation_of_a_carchive_object_via_the_framework)  
  
-   [Création explicite d’un objet CArchive](#_core_explicit_creation_of_a_carchive_object)  
  
##  <a name="_core_implicit_creation_of_a_carchive_object_via_the_framework"></a> Création implicite d’un objet CArchive via la structure  
 La façon la plus courante et la plus simple, consiste à laisser la structure créer un `CArchive` objet de votre document au nom de l’enregistrer, enregistrer sous, les commandes Ouvrir dans le menu fichier.  
  
 Voici ce que fait le framework lorsque l’utilisateur de votre application émet la commande Enregistrer sous dans le menu fichier :  
  
1.  Présente le **Enregistrer sous** boîte de dialogue et obtient le nom de fichier à partir de l’utilisateur.  
  
2.  Ouvre le fichier nommé par l’utilisateur comme un `CFile` objet.  
  
3.  Crée un `CArchive` objet qui pointe vers ce `CFile` objet. Lors de la création du `CArchive` de l’objet, le framework définit le mode de « stocker » (écrire, sérialiser), par opposition à « chargement » (lecture, désérialisation).  
  
4.  Appelle le `Serialize` fonction définie dans votre `CDocument`-classe dérivée, en lui passant une référence à la `CArchive` objet.  
  
 De votre document `Serialize` fonction puis écrit les données de la `CArchive` de l’objet, comme expliqué dans quelques instants. Au retour de votre `Serialize` fonction, le framework supprime le `CArchive` objet, puis le `CFile` objet.  
  
 Par conséquent, si vous laissez le framework pour créer le `CArchive` de l’objet de votre document, il vous est d’implémenter du document `Serialize` fonction qui écrit et lit vers et à partir de l’archive. Vous devez également implémenter `Serialize` pour toute `CObject`-objets dérivés qui du document `Serialize` fonction sérialise à son tour directement ou indirectement.  
  
##  <a name="_core_explicit_creation_of_a_carchive_object"></a> Création explicite d’un objet CArchive  
 En plus de la sérialisation d’un document via la structure, il existe des autres occasions, vous devez parfois un `CArchive` objet. Par exemple, vous souhaiterez peut-être sérialiser des données vers et depuis le Presse-papiers, représenté par un `CSharedFile` objet. Ou bien, vous souhaiterez utiliser une interface utilisateur pour enregistrer un fichier qui est différent de celui proposé par l’infrastructure. Dans ce cas, vous pouvez créer explicitement un `CArchive` objet. Pour cela la même manière que le framework, à l’aide de la procédure suivante.  
  
#### <a name="to-explicitly-create-a-carchive-object"></a>Pour créer explicitement un objet CArchive  
  
1.  Construire un `CFile` objet ou un objet dérivé de `CFile`.  
  
2.  Passez le `CFile` objet au constructeur pour `CArchive`, comme illustré dans l’exemple suivant :  
  
     [!code-cpp[NVC_MFCSerialization#5](../mfc/codesnippet/cpp/two-ways-to-create-a-carchive-object_1.cpp)]  
  
     Le deuxième argument de la `CArchive` constructeur est une valeur énumérée qui spécifie si l’archive doit être utilisée pour le stockage ou le chargement des données vers ou à partir du fichier. Le `Serialize` fonction d’un objet vérifie cet état en appelant le `IsStoring` fonction pour l’objet de l’archive.  
  
 Lorsque vous avez terminé le stockage ou le chargement des données vers ou depuis le `CArchive` de l’objet, fermez l’application. Bien que le `CArchive` (et `CFile`) les objets seront fermera automatiquement l’archive (et le fichier), il est conseillé de faire explicitement, car elle facilite la récupération des erreurs. Pour plus d’informations sur la gestion des erreurs, consultez l’article [Exceptions : interception et suppression des Exceptions](../mfc/exceptions-catching-and-deleting-exceptions.md).  
  
#### <a name="to-close-the-carchive-object"></a>Pour fermer l’objet CArchive  
  
1.  L’exemple suivant illustre comment fermer le `CArchive` objet :  
  
     [!code-cpp[NVC_MFCSerialization#6](../mfc/codesnippet/cpp/two-ways-to-create-a-carchive-object_2.cpp)]  
  
## <a name="see-also"></a>Voir aussi  
 [Sérialisation : sérialisation d’un objet](../mfc/serialization-serializing-an-object.md)

