---
title: 'main : démarrage du programme | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- vc.main.startup
- _tmain
dev_langs:
- C++
helpviewer_keywords:
- program startup [C++]
- entry points, program
- wmain function
- _tmain function
- startup code, main function
- main function, program startup
ms.assetid: f9581cd6-93f7-4bcd-99ec-d07c3c107dd4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d78ca2a195ac60e31e01bbe271b7f92536cc1a05
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/01/2018
ms.locfileid: "39401480"
---
# <a name="main-program-startup"></a>main : démarrage du programme
Une fonction spéciale nommée **principal** est le point de départ de l’exécution de tous les programmes C et C++. Si vous êtes l’écriture de code qui respecte le [!INCLUDE[TLA#tla_unicode](../atl-mfc-shared/reference/includes/tlasharptla_unicode_md.md)] modèle de programmation, vous pouvez utiliser `wmain`, qui est la version à caractères larges de **principal**.  
  
 Le **principal** fonction n’est pas prédéfinie par le compilateur. Elle doit être fournie dans le texte du programme.  
  
 La syntaxe de déclaration pour **principal** est  
  
```cpp 
int main();  
```  
  
 ou, éventuellement,  
  
```cpp 
int main(int argc, char *argv[], char *envp[]);  
```  
  
## <a name="microsoft-specific"></a>Section spécifique à Microsoft  
 La syntaxe de déclaration pour `wmain` est la suivante :  
  
```cpp 
int wmain( );  
```  
  
 ou, éventuellement,  
  
```cpp 
int wmain(int argc, wchar_t *argv[], wchar_t *envp[]);  
```  
  
 Vous pouvez également utiliser `_tmain`, qui est définie dans TCHAR.h. `_tmain` correspond à **principal** , sauf si _UNICODE est défini. Dans ce cas, `_tmain` est résolu à `wmain`.  
  
 Vous pouvez également le **principal** et `wmain` fonctions peuvent être déclarées comme retournant **void** (aucune valeur de retour). Si vous déclarez **principal** ou `wmain` comme retournant **void**, vous ne peut pas retourner un code de sortie pour le processus parent ou le système d’exploitation en utilisant un [retourner](../cpp/return-statement-in-program-termination-cpp.md) instruction. Pour retourner un code de sortie lorsque **principal** ou `wmain` est déclaré comme **void**, vous devez utiliser le [quitter](../cpp/exit-function.md) (fonction).  
  
**FIN de la section spécifique à Microsoft**  
 Les types pour `argc` et `argv` sont définis par le langage. Les noms `argc`, `argv` et `envp` sont traditionnels, mais ne sont pas requis par le compilateur. Pour plus d’informations et un exemple, consultez [définitions d’arguments](../cpp/argument-definitions.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Mots clés](../cpp/keywords-cpp.md)   
 [Utilisation de wmain au lieu de main](../cpp/using-wmain-instead-of-main.md)   
 [restrictions relatives à main (fonction)](../cpp/main-function-restrictions.md)   
 [Analyse des arguments de ligne de commande C++](../cpp/parsing-cpp-command-line-arguments.md)