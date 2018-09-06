---
title: Concepts Active Template Library (ATL) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- ATL, about ATL
ms.assetid: a3960991-4d76-4da5-9568-3fa7fde53ff4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3bb07807934dcc5c665f0058ef869f62f0b2d3ea
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43755422"
---
# <a name="active-template-library-atl-concepts"></a>Concepts ATL (Active Template Library)

La bibliothèque ATL (Active Template) est un ensemble de classes C++ basées sur modèle qui vous permettent de créer des objets de composant COM (Object Model) petits et rapides. Il prend en charge les principales fonctionnalités COM, y compris les implémentations stocks, les interfaces doubles, interfaces d’énumérateur COM standard, points de connexion, interfaces détachables et contrôles ActiveX.

Si vous faites beaucoup de programmation ATL, vous souhaiterez en savoir plus sur les attributs, une nouvelle fonctionnalité dans Visual C++ .NET est conçu pour simplifier la programmation COM. Pour plus d’informations, consultez [programmation par attributs](../windows/attributed-programming-concepts.md).

## <a name="in-this-section"></a>Dans cette section

[Didacticiel ATL](../atl/active-template-library-atl-tutorial.md)  
Vous guide à travers la création d’un contrôle et illustre certains principes de base ATL dans le processus.

[Introduction à COM et ATL](../atl/introduction-to-com-and-atl.md)  
Présente les principaux concepts derrière le composant COM (Object Model). Cet article explique également brièvement ATL What ' s et lorsque vous devez l’utiliser.

[Principes de base des objets ATL COM](../atl/fundamentals-of-atl-com-objects.md)  
Décrit la relation entre les différentes classes ATL et la façon dont ces classes sont implémentées.

[Interfaces doubles et ATL](../atl/dual-interfaces-and-atl.md)  
Décrit les interfaces doubles à partir d’un point de vue ATL.

[Collections ATL et énumérateurs](../atl/atl-collections-and-enumerators.md)  
Décrit l’implémentation et la création de collections et énumérateurs dans ATL.

[Notions fondamentales du contrôle composite](../atl/atl-composite-control-fundamentals.md)  
Fournit des instructions détaillées pour la création d’un contrôle composite. Un contrôle composite est un type de contrôle ActiveX qui peut contenir des autres contrôles ActiveX ou Windows.

[FAQ sur la relation contenant-contenu des contrôles ATL](../atl/atl-control-containment-faq.md)  
Traite des questions essentielles liées à l’hébergement des contrôles avec ATL.

[Pages de propriétés ATL COM](../atl/atl-com-property-pages.md)  
Vous montre comment spécifier et implémenter les pages de propriétés COM.

[Prise en charge d’ATL pour les contrôles DHTML](../atl/atl-support-for-dhtml-controls.md)  
Fournit des instructions détaillées pour la création d’un contrôle DHTML Edit.

[ATL, points de connexion](../atl/atl-connection-points.md)  
Explique ce que sont les points de connexion et comment ATL les implémente.

[Gestion des événements et ATL](../atl/event-handling-and-atl.md)  
Décrit les étapes que vous devez prendre pour gérer les événements COM à l’aide d’ATL [IDispEventImpl](../atl/reference/idispeventimpl-class.md) et [IDispEventSimpleImpl](../atl/reference/idispeventsimpleimpl-class.md) classes.

[ATL et le marshaleur libre de threads](../atl/atl-and-the-free-threaded-marshaler.md)  
Fournit des détails sur l’option de l’Assistant objet Simple ATL qui permet à votre classe d’agréger FTM (FTM).

[Spécification du modèle de thread du projet](../atl/specifying-the-threading-model-for-a-project-atl.md)  
Décrit les macros qui sont disponibles pour contrôler les performances d’exécution apparenté au threading dans votre projet.

[ATL, classes de module](../atl/atl-module-classes.md)  
Décrit les nouvelles classes de module pour ATL 7.0. Classes de module implémentent la fonctionnalité de base requise par ATL.

[ATL, services](../atl/atl-services.md)  
Décrit les séries d’événements qui se produisent en cas d’implémentation d’un service. Aborde également certains des concepts liés au développement d’un service.

[ATL, classes de fenêtre](../atl/atl-window-classes.md)  
Décrit comment créer, superclasse et les fenêtres de sous-classe dans ATL. Les classes de fenêtre ATL ne sont pas des classes COM.

[ATL, classes de collection](../atl/atl-collection-classes.md)  
Décrit comment utiliser des tableaux et des mappages dans ATL.

[Le composant de Registre ATL (inscription)](../atl/atl-registry-component-registrar.md)  
Traite les scripts de syntaxe et les paramètres remplaçables ATL. Il explique également comment configurer un lien statique vers le bureau d’enregistrement.

[Programmation avec ATL et le code C Run-Time](../atl/programming-with-atl-and-c-run-time-code.md)  
Décrit les avantages de la liaison de manière statique ou dynamique à la bibliothèque Runtime C (CRT).

[Programmation avec CComBSTR](../atl/programming-with-ccombstr-atl.md)  
Décrit plusieurs situations nécessitant une attention lors de la programmation avec `CComBSTR`.

[Référence d’encodage](../atl/atl-encoding-reference.md)  
Fournit des fonctions et macros qui prennent en charge de codage dans une plage de normes Internet communes telles qu’uuencode, hexadécimal et UTF-8 dans atlenc.h ainsi que.

[Référence des utilitaires](../atl/atl-utilities-reference.md)  
Fournit du code pour manipuler des chemins d’accès et les URL sous la forme de [CPathT](../atl/reference/cpatht-class.md) et [CUrl](../atl/reference/curl-class.md). Un pool de threads, [CThreadPool](../atl/reference/cthreadpool-class.md), peut être utilisé dans vos propres applications. Vous trouverez ce code dans atlpath.h et atlutil.h.

## <a name="related-sections"></a>Rubriques connexes

[Exemples ATL](../visual-cpp-samples.md)  
Fournit des descriptions et des liens vers des exemples de programmes ATL.

[Création d’un projet ATL](../atl/reference/creating-an-atl-project.md)  
Contient des informations sur l’Assistant Projet ATL.

[Assistant Contrôle ATL](../atl/reference/atl-control-wizard.md)  
Explique comment ajouter des classes.

[Programmation par attributs](../windows/attributed-programming-concepts.md)  
Fournit une vue d’ensemble sur l’utilisation d’attributs pour simplifier la programmation COM et une liste de liens vers des rubriques plus détaillées.

[Vue d’ensemble des classes ATL](../atl/atl-class-overview.md)  
Fournit des informations de référence et des liens vers les classes ATL.

