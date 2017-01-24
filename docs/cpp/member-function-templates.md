---
title: "Mod&#232;les de fonctions membres | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "modèles de fonctions, fonctions membres"
ms.assetid: 83d51835-6a27-40ed-997c-7d90dc9182d8
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Mod&#232;les de fonctions membres
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Le terme « modèle membre » fait référence aux modèles de fonction membre et aux modèles de classes imbriqués.  Les modèles de fonction membre sont des fonctions de modèle qui sont membres d'une classe ou d'un modèle de classe.  Pour plus d'informations, consultez [Modèles de classe imbriqués](../Topic/Nested%20Class%20Templates.md).  
  
 Les fonctions membres peuvent être des modèles de fonction dans plusieurs contextes.  Toutes les fonctionnalités des modèles de classe sont génériques, mais ne sont pas appelés modèles membres ou modèles de fonction membre.  Si ces fonctions membres prennent leurs propres arguments template, elles sont considérées comme des modèles de fonction membre.  Pour plus d'informations, consultez [Fonctions membres des classes de modèles](../Topic/Member%20Functions%20of%20Template%20Classes.md).  
  
## Exemple  
 Les modèles de fonction membre de classes de modèles ou de classes non basées sur un modèle sont déclarés comme modèles de fonction avec leurs paramètres de modèle.  
  
```  
// member_function_templates.cpp  
struct X  
{  
   template <class T> void mf(T* t) {}  
};  
  
int main()  
{  
   int i;  
   X* x = new X();  
   x->mf(&i);  
}  
```  
  
## Exemple  
 L'exemple suivant montre un modèle de fonction membre d'une classe de modèle.  
  
```  
// member_function_templates2.cpp  
template<typename T>  
class X  
{  
public:  
   template<typename U>  
   void mf(const U &u)  
   {  
   }  
};  
  
int main()  
{  
}  
```  
  
## Exemple  
 En outre, dans Visual Studio .NET 2003 et versions ultérieures, les modèles membres peuvent également être définis en dehors d'une classe.  
  
```  
// defining_member_templates_outside_class.cpp  
template<typename T>  
class X  
{  
public:  
   template<typename U>  
   void mf(const U &u);  
};  
  
template<typename T> template <typename U>  
void X<T>::mf(const U &u)  
{  
}  
  
int main()  
{  
}  
```  
  
## Exemple  
 Les classes locales ne doivent pas avoir de modèles membres.  
  
 Les fonctions des modèles membres ne peuvent pas être des fonctions virtuelles et ne peuvent pas remplacer des fonctions virtuelles d'une classe de base lorsqu'elles sont déclarées avec le même nom qu'une fonction virtuelle d'une classe de base.  
  
 Visual C\+\+ .NET 2003 introduit la prise en charge des conversions définies par l'utilisateur basées sur un modèle.  L'exemple suivant fonctionne dans Visual C\+\+ .NET 2003, comme indiqué dans la norme.  
  
```  
// templated_user_defined_conversions.cpp  
template <class T>  
struct S  
{  
   template <class U> operator S<U>()  
   {  
      return S<U>();  
   }  
};  
  
int main()  
{  
   S<int> s1;  
   S<long> s2 = s1;  // Convert s1 using UDC and copy constructs S<long>.  
}  
```  
  
## Voir aussi  
 [Modèles de fonctions](../cpp/function-templates.md)