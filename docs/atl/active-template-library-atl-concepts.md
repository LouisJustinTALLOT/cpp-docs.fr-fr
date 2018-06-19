---
title: Concepts de Active Template Library (ATL) | Documents Microsoft
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
ms.openlocfilehash: 5636f92df42116b838c24c21d81f0b320f7d69c1
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32358112"
---
# <a name="active-template-library-atl-concepts"></a>Concepts ATL (Active Template Library)
La bibliothèque ATL (Active Template) est un ensemble de classes C++ basées sur des modèles qui vous permettent de créer des objets de modèle COM (Component Object) petits et rapides. Il prend en charge les principales fonctionnalités COM, y compris les implémentations stock, les interfaces doubles, les interfaces d’énumérateurs COM standards, points de connexion, interfaces détachables et des contrôles ActiveX.  
  
 Si vous procédez à un grand nombre de programmation ATL, vous devez en savoir plus sur les attributs, une nouvelle fonctionnalité de Visual C++ .NET est conçu pour simplifier la programmation COM. Pour plus d’informations, consultez [programmation par attributs](../windows/attributed-programming-concepts.md).  
  
## <a name="in-this-section"></a>Dans cette section  
 [Didacticiel ATL](../atl/active-template-library-atl-tutorial.md)  
 Vous guide tout au long de la création d’un contrôle et illustre certaines notions de base ATL dans le processus.  
  
 [Introduction à COM et ATL](../atl/introduction-to-com-and-atl.md)  
 Présente les principaux concepts derrière le modèle COM (Component Object). Cet article explique également brièvement les nouveautés ATL et lorsque vous devez l’utiliser.  
  
 [Principes de base des objets ATL COM](../atl/fundamentals-of-atl-com-objects.md)  
 Décrit la relation entre les différentes classes ATL et comment ces classes sont implémentées.  
  
 [Interfaces doubles et ATL](../atl/dual-interfaces-and-atl.md)  
 Décrit les interfaces doubles à partir d’un point de vue ATL.  
  
 [Collections ATL et énumérateurs](../atl/atl-collections-and-enumerators.md)  
 Décrit l’implémentation et la création de collections et énumérateurs dans ATL.  
  
 [Principes de base des contrôles composites](../atl/atl-composite-control-fundamentals.md)  
 Fournit des instructions détaillées pour la création d’un contrôle composite. Un contrôle composite est un type de contrôle ActiveX qui peut contenir les autres contrôles ActiveX ou Windows.  
  
 [FAQ sur la relation contenant-contenu des contrôles ATL](../atl/atl-control-containment-faq.md)  
 Traite des questions essentielles relatives à l’hébergement des contrôles ATL  
  
 [Pages de propriétés ATL COM](../atl/atl-com-property-pages.md)  
 Vous montre comment spécifier et implémenter les pages de propriétés COM.  
  
 [Prise en charge d’ATL pour les contrôles DHTML](../atl/atl-support-for-dhtml-controls.md)  
 Fournit des instructions détaillées pour la création d’un contrôle DHTML.  
  
 [ATL, points de connexion](../atl/atl-connection-points.md)  
 Explique ce que sont les points de connexion et comment ATL les implémente.  
  
 [Gestion des événements et ATL](../atl/event-handling-and-atl.md)  
 Décrit les étapes que vous devez suivre pour gérer des événements COM à l’aide d’ATL [IDispEventImpl](../atl/reference/idispeventimpl-class.md) et [IDispEventSimpleImpl](../atl/reference/idispeventsimpleimpl-class.md) classes.  
  
 [ATL et le marshaleur libre de threads](../atl/atl-and-the-free-threaded-marshaler.md)  
 Fournit des détails sur l’option de l’Assistant objet Simple ATL qui permet à votre classe d’agréger FTM (FTM).  
  
 [Spécification du modèle de thread du projet](../atl/specifying-the-threading-model-for-a-project-atl.md)  
 Décrit les macros qui sont disponibles pour contrôler les performances d’exécution associées aux threads de votre projet.  
  
 [ATL, classes de module](../atl/atl-module-classes.md)  
 Décrit les nouvelles classes de module pour ATL 7.0. Classes de module implémentent la fonctionnalité de base requise par ATL.  
  
 [ATL, services](../atl/atl-services.md)  
 Traite de la série d’événements qui se produisent lors de l’implémentation d’un service. Aborde également certains des concepts liés au développement d’un service.  
  
 [ATL, classes de fenêtre](../atl/atl-window-classes.md)  
 Décrit comment créer et la superclasse, sous-classer les fenêtres dans ATL. Les classes de fenêtre ATL ne sont pas des classes COM.  
  
 [ATL, classes de collection](../atl/atl-collection-classes.md)  
 Décrit comment utiliser des tableaux et des mappages dans ATL.  
  
 [Le composant de Registre ATL (inscription)](../atl/atl-registry-component-registrar.md)  
 Traite des scripts de syntaxe et les paramètres remplaçables ATL. Elle explique également comment configurer un lien statique vers le bureau d’enregistrement.  
  
 [Programmation avec ATL et le code C Run-Time](../atl/programming-with-atl-and-c-run-time-code.md)  
 Explique les avantages de lier statiquement ou dynamiquement à la bibliothèque Runtime C (CRT).  
  
 [Programmation avec CComBSTR](../atl/programming-with-ccombstr-atl.md)  
 Décrit plusieurs situations nécessitant une attention lors de la programmation avec `CComBSTR`.  
  
 [Référence d’encodage](../atl/atl-encoding-reference.md)  
 Fournit des fonctions et des macros qui prennent en charge l’encodage dans l’étendue des normes Internet communes telles qu’uuencode, hexadécimal et UTF-8 dans atlenc.h.  
  
 [Référence des utilitaires](../atl/atl-utilities-reference.md)  
 Fournit du code pour la manipulation d’URL et les chemins d’accès sous la forme de [CPathT](../atl/reference/cpatht-class.md) et [CUrl](../atl/reference/curl-class.md). Un pool de threads, [CThreadPool](../atl/reference/cthreadpool-class.md), peut être utilisé dans vos propres applications. Vous trouverez ce code dans atlpath.h et atlutil.h.  
  
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

