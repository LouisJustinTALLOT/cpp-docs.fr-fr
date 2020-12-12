---
description: 'En savoir plus sur : @ (spécifier un fichier réponse du compilateur)'
title: '@ (Spécifier un fichier réponse du compilateur)'
ms.date: 11/04/2016
f1_keywords:
- '@'
helpviewer_keywords:
- response files, C/C++ compiler
- '@ compiler option'
- cl.exe compiler, specifying response files
ms.assetid: 400fffee-909d-4f60-bf76-45833e822685
ms.openlocfilehash: bd2859f7973723d93594693902e92ac3530d73ff
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97182890"
---
# <a name="-specify-a-compiler-response-file"></a>@ (Spécifier un fichier réponse du compilateur)

Spécifie un fichier réponse du compilateur.

## <a name="syntax"></a>Syntaxe

> **\@**<em>response_file</em>

## <a name="arguments"></a>Arguments

*response_file*<br/>
Fichier texte contenant les commandes du compilateur.

## <a name="remarks"></a>Notes

Un fichier réponse peut contenir toutes les commandes que vous spécifiez sur la ligne de commande. Cela peut être utile si vos arguments de ligne de commande dépassent 127 caractères.

Il n’est pas possible de spécifier l' **\@** option à partir d’un fichier réponse. Autrement dit, un fichier réponse ne peut pas incorporer un autre fichier réponse.

À partir de la ligne de commande, vous pouvez spécifier autant d’options de fichier réponse (par exemple `@respfile.1 @respfile.2` ) que vous le souhaitez.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

- Un fichier réponse ne peut pas être spécifié à partir de l’environnement de développement et doit être spécifié sur la ligne de commande.

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Cette option du compilateur ne peut pas être modifiée par programmation.

## <a name="see-also"></a>Voir aussi

[Options du compilateur MSVC](compiler-options.md)<br/>
[Syntaxe Command-Line du compilateur MSVC](compiler-command-line-syntax.md)
