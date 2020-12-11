---
description: 'En savoir plus sur : modification du contrôle ATL DHTML'
title: Modification du contrôle ATL DHTML
ms.date: 11/04/2016
helpviewer_keywords:
- HTML controls, modifying
- DHTML controls
- DHTML controls, modifying
ms.assetid: c053f35f-8629-4600-9595-721f5956777a
ms.openlocfilehash: 7ae9c102addd7a33341a8f16105a3581de10481e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97159451"
---
# <a name="modifying-the-atl-dhtml-control"></a>Modification du contrôle ATL DHTML

L’Assistant contrôle ATL fournit un code de démarrage qui vous permet de générer et d’exécuter le contrôle. vous pouvez ainsi voir comment les méthodes sont écrites dans les fichiers projet et comment le DHTML appelle le code C++ du contrôle à l’aide des méthodes de distribution. Vous pouvez ajouter n’importe quelle méthode de répartition à l’interface. Ensuite, vous pouvez appeler les méthodes dans la ressource HTML.

## <a name="to-modify-the-atl-dhtml-control"></a>Pour modifier le contrôle ATL DHTML

1. Dans **affichage de classes**, développez le projet de contrôle.

   Notez que l’interface qui se termine par « UI » a une méthode, `OnClick` . L’interface qui ne se termine pas par « UI » n’a pas de méthode.

1. Ajoutez une méthode appelée `MethodInvoked` à l’interface qui ne se termine pas par « UI ».

   Cette méthode sera ajoutée à l’interface utilisée dans le conteneur de contrôle pour l’interaction de conteneur, et non à l’interface utilisée par DHTML pour interagir avec le contrôle. Seul le conteneur peut appeler cette méthode.

1. Recherchez la méthode extraite dans le fichier. cpp et ajoutez du code pour afficher une boîte de message, par exemple :

   [!code-cpp[NVC_ATL_COM#5](../atl/codesnippet/cpp/modifying-the-atl-dhtml-control_1.cpp)]

1. Ajoutez une autre méthode appelée `HelloHTML` , uniquement cette fois-ci, ajoutez-la à l’interface qui se termine par « UI ». Recherchez la méthode extraite `HelloHTML` dans le fichier. cpp et ajoutez du code pour afficher une boîte de message, par exemple :

   [!code-cpp[NVC_ATL_COM#6](../atl/codesnippet/cpp/modifying-the-atl-dhtml-control_2.cpp)]

1. Ajoutez une troisième méthode, `GoToURL` , à l’interface qui ne se termine pas par « UI ». Implémentez cette méthode en appelant [IWebBrowser2 :: Navigate](/previous-versions//aa752133\(v=vs.85\)), comme suit :

   [!code-cpp[NVC_ATL_COM#7](../atl/codesnippet/cpp/modifying-the-atl-dhtml-control_3.cpp)]

   Vous pouvez utiliser les `IWebBrowser2` méthodes, car ATL fournit un pointeur vers cette interface pour vous dans votre fichier. h.

Ensuite, modifiez la ressource HTML pour appeler les méthodes que vous avez créées. Vous allez ajouter trois boutons pour appeler ces méthodes.

## <a name="to-modify-the-html-resource"></a>Pour modifier la ressource HTML

1. Dans **Explorateur de solutions**, double-cliquez sur le fichier. htm pour afficher la ressource HTML.

   Examinez le code HTML, en particulier les appels aux méthodes de distribution Windows externes. Le code HTML appelle la méthode du projet `OnClick` , et les paramètres indiquent le corps du contrôle ( `theBody` ) et la couleur à assigner (" `red` "). Le texte qui suit l’appel de méthode est l’étiquette qui apparaît sur le bouton.

1. Ajoutez une autre `OnClick` méthode, modifiez uniquement la couleur. Par exemple :

    ```html
    <br>
    <br>
    <BUTTON onclick='window.external.OnClick(theBody, "white");'>Refresh</BUTTON>
    ```

   Cette méthode crée un bouton, intitulé **Actualiser**, sur lequel l’utilisateur peut cliquer pour ramener le contrôle à l’arrière-plan blanc d’origine.

1. Ajoutez l’appel à la `HelloHTML` méthode que vous avez créée. Par exemple :

    ```html
    <br>
    <br>
    <BUTTON onclick='window.external.HelloHTML();'>HelloHTML</BUTTON>
    ```

   Cette méthode crée un bouton intitulé **HelloHTML**, sur lequel l’utilisateur peut cliquer pour afficher la `HelloHTML` boîte de message.

Vous pouvez maintenant générer et [tester le contrôle DHTML modifié](../atl/testing-the-modified-atl-dhtml-control.md).

## <a name="see-also"></a>Voir aussi

[Prise en charge pour un contrôle DHTML](../atl/atl-support-for-dhtml-controls.md)
