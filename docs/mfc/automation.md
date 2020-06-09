---
title: Automatisation
ms.date: 11/04/2016
helpviewer_keywords:
- Automation servers, about Automation servers
- clients, Automation
- programmatic control [MFC]
- properties [MFC], Automation
- MFC, COM support
- OLE Automation
- Automation
- servers [MFC], Automation
- Automation clients
- sample applications [MFC], Automation
- methods [MFC]
- passing parameters, Automation
- Automation method [MFC]
- Automation, passing parameters
- Automation property [MFC]
- MFC COM, Automation
- methods [MFC], Automation
ms.assetid: 329117f0-c1aa-4680-a901-bfb71277dfba
ms.openlocfilehash: e5790be14f26f59c2b51b339c8bee7c5eca7d692
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84616515"
---
# <a name="automation"></a>Automatisation

Automation (anciennement appelé OLE Automation) permet à une application de manipuler des objets implémentés dans une autre application, ou d'exposer des objets pour qu'ils puissent être manipulés.

[Serveur Automation](automation-servers.md) est une application (un type de serveur COM) qui affiche ses fonctionnalités via des interfaces COM vers d'autres applications, appelées [Clients Automation](automation-clients.md). L'exposition permet aux clients Automation d'automatiser certaines fonctions en accédant directement aux objets et utilisant les services qu'ils fournissent.

Les serveurs et les clients Automation utilisent des interfaces COM qui sont toujours dérivées de `IDispatch` et prennent et retournent un ensemble de types de données appelés types Automation. Vous pouvez automatiser un objet qui expose une interface Automation, en fournissant les méthodes et les propriétés auxquelles vous pouvez accéder à partir d'autres applications. Automation est disponible pour les objets OLE et COM. L'objet automatisé peut être local ou distant (sur un ordinateur accessible depuis un réseau) ; il existe deux catégories d'automatisation :

- Automation (local).

- Automation à distance (sur un réseau, en utilisant DCOM (Distributed COM)).

Exposer des objets est judicieux si les applications offrent des fonctionnalités utiles pour d'autres applications. Par exemple, un contrôle ActiveX est un type de serveur Automation ; l'application qui héberge le contrôle ActiveX est le client Automation de ce contrôle.

À titre d'exemple, un traitement de texte peut exposer ses fonctionnalités de contrôle d'orthographe à d'autres programmes. L'exposition des objets permet aux fournisseurs d'améliorer leurs applications en utilisant les fonctions déjà existantes d'autres applications. De cette manière, Automation applique certains principes de programmation orientée objet, tels que la réutilisabilité et l'encapsulation, au niveau des applications elles-mêmes.

Le support que Automation offre aux utilisateurs et aux fournisseurs de solutions est plus important. En exposant des fonctionnalités d'application via une interface commune et bien définie, Automation permet de générer des solutions complètes dans un seul langage de programmation général, tel que Microsoft Visual Basic, et non pas dans des macro-langages spécifiques à chaque application.

De nombreuses applications commerciales, telles que Microsoft Excel et Microsoft Visual C++, vous permettent d'automatiser plusieurs de leurs fonctionnalités. Par exemple, dans Visual C++, vous pouvez écrire des macros en VBScript pour automatiser la génération, certains aspects de la modification de code ou des tâches de débogage.

## <a name="passing-parameters-in-automation"></a><a name="_core_passing_parameters_in_automation"></a> Passage de paramètres dans Automation

Une difficulté dans la création de méthodes Automation permet de fournir un mécanisme uniforme "sûr" pour passer des données entre les serveurs et les clients Automation. Automation utilise le type **VARIANT** pour passer des données. Le type **VARIANT** est une union avec balises. Il comprend des données membre pour la valeur (il s'agit d'une union anonyme C++) et des données membre indiquant le type d'informations stockées dans l'union. Le type **VARIANT** prend en charge plusieurs types de données standard : des entiers codés sur 2 et 4 octets, des nombres à virgule flottante codés sur 4 et 8 octets, des chaînes et des valeurs booléennes. En outre, il prend en charge les types **HRESULT** (codes d’erreur OLE), **Currency** (type numérique à virgule fixe) et **Date** (date et heure absolues), ainsi que les pointeurs vers `IUnknown` les `IDispatch` interfaces et.

Le type **VARIANT** est encapsulé dans la classe [COleVariant](reference/colevariant-class.md) . Les classes **CURRENCY** et **DATE** prises en charge sont encapsulées dans les classes [COleCurrency](reference/colecurrency-class.md) et [COleDateTime](../atl-mfc-shared/reference/coledatetime-class.md) .

## <a name="automation-samples"></a>Exemples d'utilisation Automation

- [AUTOCLIK](../overview/visual-cpp-samples.md) Utilisez cet exemple pour apprendre les techniques d'Automation et en guise de base pour découvrir Automation à distance.

- [ACDUAL](../overview/visual-cpp-samples.md) Ajoute des interfaces doubles à une application de serveur Automation.

- [CALCDRIV](../overview/visual-cpp-samples.md) Application cliente Automation gérant MFCCALC.

- [INPROC](../overview/visual-cpp-samples.md) Illustre une application serveur Automation en fonctionnement.

- [IPDRIVE](../overview/visual-cpp-samples.md) Application Automation gérant INPROC.

- [MFCCALC](../overview/visual-cpp-samples.md) Illustre une application cliente Automation.

## <a name="what-do-you-want-to-know-more-about"></a>Que voulez-vous en savoir plus sur

- [Clients Automation](automation-clients.md)

- [Serveurs Automation](automation-servers.md)

- [OLE](ole-in-mfc.md)

- [technologie active](mfc-com.md)

## <a name="what-do-you-want-to-do"></a>Tu veux faire quoi

- [Ajouter une classe Automation](automation-servers.md)

- [Utiliser les bibliothèques de types](automation-clients-using-type-libraries.md)

- [Accéder aux serveurs Automation](automation-servers.md)

- [Implémenter des clients Automation en C++](automation-clients.md)

## <a name="see-also"></a>Voir aussi

[MFC COM](mfc-com.md)
