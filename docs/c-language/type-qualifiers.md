---
title: "Qualificateurs de type | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "const (mot clé) (C)"
  - "mémoire, accéder à l'aide de mémoire volatile"
  - "qualificateurs pour les types"
  - "qualificateurs de type"
  - "volatile (mot clé) (C)"
  - "volatile (mot clé) (C), qualificateur de type"
  - "volatile (mot clé) (C), spécificateur de type"
ms.assetid: bb4c6744-1dd7-40a8-b4eb-f5585be30908
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# Qualificateurs de type
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Les qualificateurs de type fournissent une des deux propriétés à un identificateur.  Le qualificateur de type **const** déclare un objet comme étant non modifiable.  Le qualificateur de type `volatile` déclare un élément dont la valeur peut légitimement être modifiée par quelque chose non contrôlé par le programme dans lequel il apparaît, par exemple un thread s'exécutant simultanément.  
  
 Les deux qualificateurs de type, **const** et `volatile`, ne peuvent apparaître qu'une seule fois dans une déclaration.  Ils peuvent apparaître avec n'importe quel spécificateur de type. Toutefois, ils ne peuvent pas apparaître après la première virgule dans une déclaration d'éléments multiples.  Par exemple, les déclarations suivantes sont autorisées :  
  
```  
typedef volatile int VI;  
const int ci;  
```  
  
 Les déclarations suivantes ne sont pas autorisées :  
  
```  
typedef int *i, volatile *vi;  
float f, const cf;     
```  
  
 Les qualificateurs de type sont appropriés uniquement lors de l'accès à des identificateurs sous la forme d'l\-values dans des expressions.  Consultez [Expressions L\-value et r\-value](../c-language/l-value-and-r-value-expressions.md) pour plus d'informations sur les l\-values et les expressions.  
  
## Syntaxe  
 *type\-qualifier* :  
 **constvolatile**  
  
 Voici les déclarations **const** et `volatile` autorisées :  
  
```  
int const *p_ci;       /* Pointer to constant int */  
int const (*p_ci);     /* Pointer to constant int */  
int *const cp_i;       /* Constant pointer to int */  
int (*const cp_i);     /* Constant pointer to int */  
int volatile vint;     /* Volatile integer        */  
```  
  
 Si la spécification d'un type tableau inclut des qualificateurs de type, l'élément est qualifié, pas le type tableau.  Si la spécification du type de fonction comprend des qualificateurs, le comportement est non défini.  Ni `volatile` ni **const** n'ont d'incidence sur la plage de valeurs ou les propriétés arithmétiques de l'objet.  
  
 La liste suivante explique comment utiliser **const** et `volatile`.  
  
-   Le mot clé **const** peut être utilisé pour modifier tout type fondamental ou d'agrégat, ou un pointeur vers un objet de tout type, ou un `typedef`.  Si un élément est déclaré avec uniquement le qualificateur de type **const**, son type est considéré comme étant **const int**.  Une variable **const** peut être initialisée ou placée dans une zone de stockage en lecture seule.  Le mot clé **const** est utile pour déclarer des pointeurs vers **const** puisqu'il interdit à la fonction de modifier le pointeur d'une manière ou d'une autre.  
  
-   Le compilateur suppose que, à tout moment dans le programme, une variable `volatile` est accessible par un processus inconnu qui utilise ou modifie sa valeur.  Par conséquent, indépendamment des optimisations spécifiées sur la ligne de commande, le code pour chaque assignation ou référence d'une variable `volatile` doit être généré même s'il semble n'avoir aucun effet.  
  
     Si `volatile` est utilisé seul, `int` est pris par défaut.  Le spécificateur de type `volatile` peut être utilisé pour fournir un accès fiable aux emplacements de mémoire spéciaux.  Utilisez `volatile` avec des objets de données accessibles ou modifiables par les gestionnaires de signaux, en exécutant simultanément des programmes, ou par un matériel spécial tel que les registres de contrôle d'E\/S mappé en mémoire.  Vous pouvez déclarer une variable comme `volatile` pour toute sa durée de vie, ou vous pouvez effectuer un cast d'une référence unique pour qu'elle soit `volatile`.  
  
-   Un élément peut être **const** et `volatile`, auquel cas il ne peut pas être légitimement modifié par son propre programme, mais par un processus asynchrone.  
  
## Voir aussi  
 [Déclarations et types](../c-language/declarations-and-types.md)