---
title: "Les informations HRESULT dans le code manag&#233; | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "HRESULT, VSPackages managé"
  - "VSPackages, Les informations HRESULT"
ms.assetid: 0795ee94-17a8-4327-bf57-27cd5e312a4c
caps.latest.revision: 29
caps.handback.revision: 29
manager: "douge"
---
# Les informations HRESULT dans le code manag&#233;
L’interaction entre le code managé et COM peut entraîner des problèmes quand vous rencontrez des valeurs de retour HRESULT.  
  
 Dans une interface COM, une valeur de retour HRESULT peut jouer ces rôles :  
  
-   Fournir des informations d’erreur \(par exemple, <xref:Microsoft.VisualStudio.VSConstants.E_INVALIDARG>\).  
  
-   Fournir des informations d’état sur le comportement normal du programme.  
  
 Quand COM appelle du code managé, les HRESULT peuvent entraîner ces problèmes :  
  
-   Les fonctions COM qui retournent des valeurs HRESULT inférieures à zéro \(codes d’échec\) génèrent des exceptions.  
  
-   Les méthodes COM qui retournent régulièrement deux codes de réussite différents ou plus, par exemple, <xref:Microsoft.VisualStudio.VSConstants.S_OK> ou <xref:Microsoft.VisualStudio.VSConstants.S_FALSE>, ne peuvent pas être distinguées.  
  
 Étant donné qu’un grand nombre des fonctions COM [!INCLUDE[vsipsdk](../mfc/includes/vsipsdk_md.md)] retournent des valeurs HRESULT inférieures à zéro ou des codes de réussite différents, les assemblys d’interopérabilité [!INCLUDE[vsipsdk](../mfc/includes/vsipsdk_md.md)] ont été écrits de sorte que les signatures de méthode soient conservées. Toutes les méthodes d’interopérabilité [!INCLUDE[vsipsdk](../mfc/includes/vsipsdk_md.md)] sont de type `int`. Des valeurs HRESULT sont transmises via la couche d’interopérabilité sans modification et sans générer d’exceptions.  
  
 Étant donné qu’une fonction COM retourne un HRESULT à la méthode managée qui l’appelle, la méthode qui appelle doit vérifier le HRESULT et lever des exceptions si nécessaire.  
  
## Gestion des HRESULT retournés au code managé à partir de COM  
 Quand vous appelez une interface COM à partir de code managé, examinez la valeur HRESULT et levez une exception si nécessaire. La classe <xref:Microsoft.VisualStudio.ErrorHandler> contient la méthode <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> qui lève une exception COM, selon la valeur HRESULT qui lui est passée.  
  
 Par défaut, <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> lève une exception dès lors qu’elle est passée à un HRESULT qui a une valeur inférieure à zéro. Dans les cas où ces valeurs HRESULT sont des valeurs acceptables et quand aucune exception ne doit être levée, les valeurs des HRESULT supplémentaires doivent être passées à <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> une fois les valeurs testées. Si la valeur HRESULT testée correspond à une valeur HRESULT explicitement passée à <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>, aucune exception n’est levée.  
  
> [!NOTE]
>  La classe <xref:Microsoft.VisualStudio.VSConstants> contient des constantes pour les valeurs HRESULT courantes \(comme <xref:Microsoft.VisualStudio.VSConstants.S_OK> et <xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL>\) et les valeurs HRESULT [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] \(comme <xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA> et <xref:Microsoft.VisualStudio.VSConstants.VS_E_UNSUPPORTEDFORMAT>\).<xref:Microsoft.VisualStudio.VSConstants> fournit également les méthodes <xref:Microsoft.VisualStudio.ErrorHandler.Succeeded%2A> et <xref:Microsoft.VisualStudio.ErrorHandler.Failed%2A> qui correspondent aux macros SUCCEEDED et FAILED dans COM.  
  
 Par exemple, considérez l’appel de fonction suivant, dans lequel <xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL> est une valeur de retour acceptable, alors que les autres valeurs HRESULT inférieures à zéro représentent une erreur.  
  
 [!code-vb[VSSDKHRESULTInformation#1](../misc/codesnippet/VisualBasic/hresult-information-in-managed-code_1.vb)]
 [!code-cs[VSSDKHRESULTInformation#1](../misc/codesnippet/CSharp/hresult-information-in-managed-code_1.cs)]  
  
 S’il existe plusieurs valeurs de retour acceptables, les autres valeurs HRESULT peuvent être simplement ajoutées à la liste dans l’appel à <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>.  
  
 [!code-vb[VSSDKHRESULTInformation#2](../misc/codesnippet/VisualBasic/hresult-information-in-managed-code_2.vb)]
 [!code-cs[VSSDKHRESULTInformation#2](../misc/codesnippet/CSharp/hresult-information-in-managed-code_2.cs)]  
  
## Retour de valeurs HRESULT à COM à partir de code managé  
 Si aucune exception ne se produit, le code managé retourne <xref:Microsoft.VisualStudio.VSConstants.S_OK> à la fonction COM qui l’a appelé. COM interop prend en charge les exceptions courantes qui sont fortement typées dans du code managé. Par exemple, une méthode qui reçoit un argument `null` inacceptable lève une <xref:System.ArgumentNullException>.  
  
 Si vous ne savez pas quelle exception lever, alors que vous connaissez la valeur HRESULT à retourner à COM, vous pouvez utiliser la méthode <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> pour lever une exception appropriée. Cela fonctionne même avec une erreur non standard, par exemple, <xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA>.<xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> essaie de mapper la valeur HRESULT qui lui est passée sur une exception fortement typée. Si ce n’est pas possible, une exception COM générique est levée. Le résultat final est que la valeur HRESULT que vous passez à <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> à partir du code managé est retournée à la fonction COM qui l’a appelée.  
  
> [!NOTE]
>  Les exceptions nuisent aux performances et ont vocation à indiquer des conditions anormales pour le programme. Les conditions qui se produisent souvent doivent être gérées instantanément, au lieu de lever une exception.  
  
## Voir aussi  
 [VSPackages gérés](../misc/managed-vspackages.md)   
 [Interoperating with Unmanaged Code](../Topic/Interoperating%20with%20Unmanaged%20Code.md)   
 [How to: Map HRESULTs and Exceptions](../Topic/How%20to:%20Map%20HRESULTs%20and%20Exceptions.md)   
 [Génération de composants COM pour l’interopérabilité](http://msdn.microsoft.com/fr-fr/7a2c657a-cfef-40f0-bed3-7c2c0ac4abdf)   
 [VSPackages gérés](../misc/managed-vspackages.md)