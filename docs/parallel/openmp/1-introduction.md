---
title: 1. Présentation | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: c42e72bc-0e31-4b1c-b670-cd82673c0c5a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4ce963d312d145e26567a5902f32e45735eb1d89
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46438416"
---
# <a name="1-introduction"></a>1. Introduction

Ce document spécifie une collection de directives de compilateur, les fonctions de bibliothèque et les variables d’environnement qui peuvent être utilisées pour spécifier le parallélisme de mémoire partagée dans les programmes C et C++. La fonctionnalité décrite dans ce document est collectivement appelée le *OpenMP C/C++ Interface API (Application Program)*. L’objectif de cette spécification est de fournir un modèle de programmation parallèle qui permet à un programme soit portable sur des architectures de mémoire partagée à partir de différents fournisseurs. L’API C/C++ OpenMP est pris en charge par les compilateurs de nombreux fournisseurs. Plus d’informations sur OpenMP, y compris le *OpenMP Fortran Application Program Interface*, vous pouvez trouver sur le site web suivant :

[http://www.openmp.org](http://www.openmp.org)

Les directives, les fonctions de bibliothèque et les variables d’environnement définies dans ce document permettra aux utilisateurs de créer et gérer tout en autorisant la portabilité des programmes parallèles. Les directives d’étendent le C et modèle de programmation séquentielle en C++ avec un seul programme plusieurs constructions de données (SPMD), les constructions de partage de travail et les constructions de synchronisation, et qu’ils prennent en charge pour le partage et la privatisation de données. Les compilateurs qui prennent en charge les API C++ OpenMP C inclut une option de ligne de commande du compilateur qui active et permet l’interprétation de toutes les directives de compilateur OpenMP.