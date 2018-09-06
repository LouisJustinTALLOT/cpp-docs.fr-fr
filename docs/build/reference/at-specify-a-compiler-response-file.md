---
title: '@ (Spécifier un fichier de réponse du compilateur) | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- '@'
dev_langs:
- C++
helpviewer_keywords:
- response files, C/C++ compiler
- '@ compiler option'
- cl.exe compiler, specifying response files
ms.assetid: 400fffee-909d-4f60-bf76-45833e822685
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 430e6372c1ca26e946c2ff26bfcfe9180dfb0dba
ms.sourcegitcommit: d10a2382832373b900b1780e1190ab104175397f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43894453"
---
# <a name="-specify-a-compiler-response-file"></a>@ (Spécifier un fichier réponse du compilateur)

Spécifie un fichier de réponse du compilateur.

## <a name="syntax"></a>Syntaxe

> **\@**<em>response_file</em>

## <a name="arguments"></a>Arguments

*response_file*  
Un fichier texte contenant les commandes du compilateur.

## <a name="remarks"></a>Notes

Un fichier réponse peut contenir toutes les commandes que vous spécifiez sur la ligne de commande. Cela peut être utile si vos arguments de ligne de commande dépassent 127 caractères.

Il n’est pas possible de spécifier le **\@** option à partir d’un fichier réponse. Autrement dit, un fichier réponse ne peut pas incorporer un autre fichier de réponse.

À partir de la ligne de commande, vous pouvez spécifier autant d’options fichier réponse (par exemple, `@respfile.1 @respfile.2`) que vous le souhaitez.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

- Un fichier réponse ne peut pas être spécifié dans l’environnement de développement et doit être spécifié sur la ligne de commande.

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Cette option du compilateur ne peut pas être modifiée par programmation.

## <a name="see-also"></a>Voir aussi

[Options du compilateur](../../build/reference/compiler-options.md)  
[Définition des options du compilateur](../../build/reference/setting-compiler-options.md)  
