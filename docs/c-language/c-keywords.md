---
title: "Mots cl&#233;s C | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "mots clés (C)"
  - "mots clés spécifiques à Microsoft"
  - "redéfinir les mots de passe"
ms.assetid: 2d932335-97bf-45cd-b367-4ae00db0ff42
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Mots cl&#233;s C
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Les « mots clés » sont des mots qui ont une signification spéciale pour le compilateur C.  Dans les phases de traduction 7 et 8, un identificateur ne peut pas avoir la même orthographe et la même casse qu'un mot clé C. \(Consultez une description des [phases de traduction](../preprocessor/phases-of-translation.md) dans *Référence du préprocesseur* ; pour obtenir des informations sur les identificateurs, consultez [Identificateurs](../c-language/c-identifiers.md).\) Le langage C utilise les mots clés suivants :  
  
|||||  
|-|-|-|-|  
|**auto**|**double**|`int`|`struct`|  
|**break**|**else**|**long**|`switch`|  
|**case**|`enum`|**register**|`typedef`|  
|`char`|`extern`|`return`|**union**|  
|**const**|**float**|**short**|`unsigned`|  
|**continue**|**for**|**signed**|`void`|  
|**default**|`goto`|`sizeof`|`volatile`|  
|**do**|**if**|**static**|`while`|  
  
 Vous ne pouvez pas redéfinir les mots clés.  Toutefois, vous pouvez spécifier du texte à substituer pour des mots clés avant la compilation, à l'aide des [directives de préprocesseur](../preprocessor/preprocessor-directives.md) C.  
  
 **Section spécifique à Microsoft**  
  
 La norme ANSI C permet de réserver les identificateurs avec deux traits de soulignement à gauche pour les implémentations du compilateur.  Par conséquent, la convention Microsoft est de faire précéder les noms des mots clés spécifiques à Microsoft de deux traits de soulignement.  Ces mots ne peuvent pas être utilisés en tant que noms d'identificateurs.  Pour obtenir une description des règles ANSI d'attribution de noms aux identificateurs, y compris l'utilisation de deux traits de soulignement, consultez [Identificateurs](../c-language/c-identifiers.md).  
  
 Les mots clés et les identificateurs spéciaux ci\-dessous sont reconnus par le compilateur Microsoft C :  
  
|||||  
|-|-|-|-|  
|`__asm`|**dllimport**2|`__int8`|`naked`2|  
|`__based`1|`__except`|`__int16`|`__stdcall`|  
|`__cdecl`|`__fastcall`|`__int32`|**thread**2|  
|`__declspec`|`__finally`|`__int64`|`__try`|  
|`dllexport`2|`__inline`|`__leave`||  
  
 1.  Le mot clé `__based` a des utilisations limitées pour les compilations 32 bits et 64 bits cibles.  
  
 2.  Ce sont des identificateurs spéciaux lorsqu'ils sont utilisés avec `__declspec` ; leur utilisation dans d'autres contextes n'est pas limitée.  
  
 Les extensions Microsoft sont activées par défaut.  Pour garantir la portabilité totale de vos programmes, vous pouvez désactiver les extensions Microsoft en spécifiant l'option \/Za \(compilation pour compatibilité ANSI\) pendant la compilation.  Dans ce cas, les mots clés spécifiques à Microsoft sont désactivés.  
  
 Lorsque les extensions Microsoft sont activées, vous pouvez utiliser les mots clés répertoriés ci\-dessus dans vos programmes.  Pour la compatibilité ANSI, la plupart de ces mots clés sont précédés de deux traits de soulignement.  Les quatre exceptions, `dllexport`, **dllimport**, `naked` et **thread**, sont utilisées uniquement avec `__declspec` et ne requièrent donc pas un double trait de soulignement à gauche.  Pour assurer la compatibilité descendante, des versions à un seul trait de soulignement sont prises en charge pour les autres mots clés.  
  
 **FIN de la section spécifique à Microsoft**  
  
## Voir aussi  
 [Éléments de C](../c-language/elements-of-c.md)