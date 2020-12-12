---
description: 'En savoir plus sur : avertissement du compilateur (niveau 1) C4678'
title: Avertissement du compilateur (niveau 1) C4678
ms.date: 11/04/2016
f1_keywords:
- C4678
helpviewer_keywords:
- C4678
ms.assetid: 0c588f34-595d-4e5c-9470-8723fca2cc06
ms.openlocfilehash: a590bd03ba73fc4f8d5421727e5e35ac1384ffaa
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97285381"
---
# <a name="compiler-warning-level-1-c4678"></a>Avertissement du compilateur (niveau 1) C4678

la classe de base 'base_type' est moins accessible que 'derived_type'

Un type public dérive d’un type privé. Si le type public est instancié dans un assembly référencé, les membres du type de base privé ne sont pas accessibles.

C4678 est accessible uniquement à l’aide de l’option de compilateur obsolète **/clr : oldSyntax**. Quand vous utilisez **/CLR**, il s’agit d’une erreur qui a une classe de base moins accessible que sa classe dérivée.
