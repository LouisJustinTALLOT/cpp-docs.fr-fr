---
description: 'En savoir plus sur les concepts suivants : Active Template Library (ATL)'
title: Concepts ATL (Active Template Library)
ms.date: 05/06/2019
helpviewer_keywords:
- ATL, about ATL
ms.assetid: a3960991-4d76-4da5-9568-3fa7fde53ff4
ms.openlocfilehash: 5437f381ea145d5474dcdba25673d4e41c60c54b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97166315"
---
# <a name="active-template-library-atl-concepts"></a>Concepts ATL (Active Template Library)

La bibliothèque ATL (Active Template Library) est un ensemble de classes C++ basées sur un modèle qui vous permettent de créer des objets COM (Component Object Model) petits et rapides. Elle assure une prise en charge spéciale des principales fonctionnalités COM, telles que les implémentations stock, interfaces doubles, interfaces d’énumérateur COM standard, points de connexion, interfaces détachables et contrôles ActiveX.

Si vous faites beaucoup de programmation ATL, vous voudrez en savoir plus sur les attributs COM et .NET, qui sont conçus pour simplifier la programmation COM. Pour plus d’informations, consultez [Programmation par attributs](../windows/attributes/cpp-attributes-com-net.md). (Les attributs COM et .NET ne doivent pas être confondus avec la fonctionnalité \[\[attribute]] de la norme C++.)

## <a name="in-this-section"></a>Dans cette section

[Introduction à COM et ATL](introduction-to-com-and-atl.md)<br/>
Présente les principaux concepts derrière le composant COM (Component Object Model). Cet article décrit aussi brièvement ATL et quand vous devez l’utiliser.

[Notions de base des objets COM ATL](fundamentals-of-atl-com-objects.md)<br/>
Décrit la relation entre les différentes classes ATL et la façon dont ces classes sont implémentées.

[Interfaces doubles et ATL](dual-interfaces-and-atl.md)<br/>
Décrit les interfaces doubles d’un point de vue ATL.

[Collections et énumérateurs ATL](atl-collections-and-enumerators.md)<br/>
Décrit l’implémentation et la création de collections et d’énumérateurs dans ATL.

[Notions de base des contrôles composites](atl-composite-control-fundamentals.md)<br/>
Fournit des instructions détaillées pour la création d’un contrôle composite. Un contrôle composite est un type de contrôle ActiveX qui peut contenir d’autres contrôles ActiveX ou Windows.

[FAQ sur la relation contenant-contenu des contrôles ATL](atl-control-containment-faq.md)<br/>
Traite des questions essentielles liées à l’hébergement des contrôles avec ATL.

[Pages de propriétés ATL COM](atl-com-property-pages.md)<br/>
Vous montre comment spécifier et implémenter les pages de propriétés COM.

[Prise en charge ATL pour les contrôles DHTML](atl-support-for-dhtml-controls.md)<br/>
Fournit des instructions détaillées pour la création d’un contrôle DHTML.

[Points de connexion ATL](atl-connection-points.md)<br/>
Explique ce que sont les points de connexion et comment ATL les implémente.

[Gestion des événements et ATL](event-handling-and-atl.md)<br/>
Décrit les étapes que vous devez suivre pour gérer les événements COM à l’aide des classes [IDispEventImpl](reference/idispeventimpl-class.md) et [IDispEventSimpleImpl](reference/idispeventsimpleimpl-class.md) d’ATL.

[ATL et le marshaleur libre de threads](atl-and-the-free-threaded-marshaler.md)<br/>
Fournit des détails sur l’option de l’Assistant Objet simple ATL qui permet à votre classe d’agréger le marshaleur libre de threads (FTM).

[Spécification du modèle de thread du projet](specifying-the-threading-model-for-a-project-atl.md)<br/>
Décrit les macros qui sont disponibles pour contrôler les performances d’exécution liées au threading dans votre projet.

[Classes de module ATL](atl-module-classes.md)<br/>
Décrit les classes de module nouvelles dans ATL 7.0. Les classes de module implémentent la fonctionnalité de base requise par ATL.

[Services ATL](atl-services.md)<br/>
Décrit les séries d’événements qui se produisent en cas d’implémentation d’un service. Aborde également certains des concepts liés au développement d’un service.

[Classes de fenêtre ATL](atl-window-classes.md)<br/>
Décrit comment créer, surclasser et sous-classer les fenêtres dans ATL. Les classes de fenêtre ATL ne sont pas des classes COM.

[Classes de collection ATL](atl-collection-classes.md)<br/>
Décrit comment utiliser des tableaux et des mappages dans ATL.

[Composant de registre ATL (inscription)](atl-registry-component-registrar.md)<br/>
Traite les paramètres remplaçables et la syntaxe de script ATL. Il explique également comment configurer un lien statique vers l’organisme d’enregistrement.

[Programmation avec des Run-Time du code ATL et C](programming-with-atl-and-c-run-time-code.md)<br/>
Décrit les avantages de la liaison de manière statique ou dynamique à la bibliothèque Runtime C (CRT).

[Programmation avec CComBSTR](programming-with-ccombstr-atl.md)<br/>
Décrit plusieurs situations nécessitant une vigilance particulière lors de la programmation avec `CComBSTR`.

[Référence d’encodage](atl-encoding-reference.md)<br/>
Fournit des fonctions et macros qui prennent en charge l’encodage dans une plage de normes Internet communes comme uuencode, le format hexadécimal et UTF-8 dans atlenc.h.

[Référence des utilitaires](atl-utilities-reference.md)<br/>
Fournit du code pour manipuler des chemins et des URL sous la forme de [CPathT](reference/cpatht-class.md) et [CUrl](reference/curl-class.md). Un pool de threads, [CThreadPool](reference/cthreadpool-class.md), peut être utilisé dans vos propres applications. Vous trouverez ce code dans atlpath.h et atlutil.h.

## <a name="related-sections"></a>Sections connexes

[Tutoriel ATL](active-template-library-atl-tutorial.md)<br/>
Vous guide tout au long de la création d’un contrôle et illustre certains principes de base ATL dans le processus.

[Exemples ATL](../overview/visual-cpp-samples.md)<br/>
Fournit des descriptions des exemples de programmes ATL et des liens vers ceux-ci.

[Création d’un projet ATL](reference/creating-an-atl-project.md)<br/>
Contient des informations sur l’Assistant Projet ATL.

[Assistant Contrôle ATL](reference/atl-control-wizard.md)<br/>
Explique comment ajouter des classes.

[Programmation par attributs](../windows/attributes/cpp-attributes-com-net.md)<br/>
Fournit une vue d’ensemble sur l’utilisation d’attributs pour simplifier la programmation COM et une liste de liens vers des rubriques plus détaillées.

[Vue d’ensemble de la classe ATL](atl-class-overview.md)<br/>
Fournit des informations de référence et des liens vers les classes ATL.
