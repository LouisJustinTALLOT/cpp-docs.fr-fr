---
description: En savoir plus sur les classes de fenêtre ATL
title: ATL, classes de fenêtre
ms.date: 11/04/2016
helpviewer_keywords:
- ATL, windows
- windows [C++], subclassing
- windows [C++], superclassing
- windows [C++], ATL
- subclassing ATL window classes
- superclassing
- superclassing, ATL
ms.assetid: 1d12b708-de3e-49d5-9e41-42fe4769fa62
ms.openlocfilehash: e8e7b8c9d8492c133c305bf46abe493d993d398c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97148549"
---
# <a name="atl-window-classes"></a>ATL, classes de fenêtre

ATL comprend plusieurs classes qui vous permettent d’utiliser et d’implémenter Windows. Ces classes, comme d’autres classes ATL, fournissent une implémentation efficace qui n’impose pas de surcharge sur votre code.

Cette section décrit les classes de fenêtre ATL et explique comment les utiliser.

## <a name="in-this-section"></a>Dans cette section

[Présentation des classes de fenêtre ATL](../atl/introduction-to-atl-window-classes.md)<br/>
Décrit brièvement chaque classe de fenêtre ATL et fournit des liens vers les documents de référence qui s’y rapportent.

[Utilisation d’une fenêtre](../atl/using-a-window.md)<br/>
Explique comment utiliser `CWindow` pour manipuler une fenêtre.

[Implémentation d’une fenêtre](../atl/implementing-a-window.md)<br/>
Décrit les gestionnaires de messages, les tables des messages et l’utilisation de `CWindowImpl` . Contient des détails sur la superclassement et le sous-classement.

[Implémentation d’une boîte de dialogue](../atl/implementing-a-dialog-box.md)<br/>
Décrit les deux méthodes d’ajout d’une classe de boîte de dialogue et montre un exemple de code.

[Utilisation des fenêtres contenues](../atl/using-contained-windows.md)<br/>
Décrit les fenêtres contenues dans ATL, qui sont des fenêtres qui délèguent leurs messages à un objet conteneur au lieu de les gérer dans leur propre classe.

[Fonctionnement des traits de fenêtre](../atl/understanding-window-traits.md)<br/>
Présente les classes de traits de fenêtre dans ATL. Ces classes fournissent une méthode simple pour standardiser les styles utilisés pour la création d’un objet Window.

## <a name="related-sections"></a>Sections connexes

[ATL](../atl/active-template-library-atl-concepts.md)<br/>
Propose des liens vers des rubriques conceptuelles traitant de la programmation à l'aide de la bibliothèque ATL (Active Template Library).

[Classes de prise en charge Windows](../atl/windows-support-classes.md)<br/>
Répertorie des classes ATL supplémentaires qui prennent en charge les fenêtres et les tables des messages dans ATL.
