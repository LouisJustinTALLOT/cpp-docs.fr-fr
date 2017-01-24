---
title: "tile_static, mot cl&#233; | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "tile_static_CPP"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "tile_static (mot clé)"
ms.assetid: d78384d4-65d9-45cf-b3df-7e904f489d06
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# tile_static, mot cl&#233;
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Le mot clé `tile_static` sert à déclarer une variable accessible par tous les threads dans une mosaïque de threads.  La durée de vie des variables commence lorsque l'exécution atteint le point de déclaration et se termine lorsque la fonction noyau est retournée.  Pour plus d'informations sur l'utilisation des mosaïques, consultez [Utilisation des mosaïques](../parallel/amp/using-tiles.md).  
  
 Le mot clé `tile_static` présente les limitations suivantes :  
  
-   Il peut être utilisé uniquement sur des variables qui sont dans une fonction ayant le modificateur `restrict(amp)`.  
  
-   Il ne peut pas être utilisé sur des variables qui sont des types pointeur ou référence.  
  
-   Une variable `tile_static` ne peut pas avoir d'initialiseur.  Les constructeurs et les destructeurs par défaut ne sont pas appelés automatiquement.  
  
-   La valeur d'une variable `tile_static` non initialisée est non définie.  
  
-   Si une variable `tile_static` est déclarée dans un graphique des appels qui est enraciné par un appel non mosaïque à `parallel_for_each`, un avertissement est généré et le comportement de la variable est non défini.  
  
## Exemple  
 L'exemple suivant montre comment une variable `tile_static` peut être utilisée pour accumuler des données sur plusieurs threads dans une mosaïque.  
  
```cpp  
  
// Sample data:  
int sampledata[] = {  
    2, 2, 9, 7, 1, 4,  
    4, 4, 8, 8, 3, 4,  
    1, 5, 1, 2, 5, 2,  
    6, 8, 3, 2, 7, 2};  
  
// The tiles:  
// 2 2    9 7    1 4  
// 4 4    8 8    3 4  
//  
// 1 5    1 2    5 2  
// 6 8    3 2    7 2  
  
// Averages:  
int averagedata[] = {   
    0, 0, 0, 0, 0, 0,   
    0, 0, 0, 0, 0, 0,   
    0, 0, 0, 0, 0, 0,   
    0, 0, 0, 0, 0, 0,   
};  
  
array_view<int, 2> sample(4, 6, sampledata);  
array_view<int, 2> average(4, 6, averagedata);  
  
parallel_for_each(  
    // Create threads for sample.extent and divide the extent into 2 x 2 tiles.  
    sample.extent.tile<2,2>(),  
    [=](tiled_index<2,2> idx) restrict(amp)  
    {  
        // Create a 2 x 2 array to hold the values in this tile.  
        tile_static int nums[2][2];  
        // Copy the values for the tile into the 2 x 2 array.  
        nums[idx.local[1]][idx.local[0]] = sample[idx.global];  
        // When all the threads have executed and the 2 x 2 array is complete, find the average.  
        idx.barrier.wait();  
        int sum = nums[0][0] + nums[0][1] + nums[1][0] + nums[1][1];  
        // Copy the average into the array_view.  
        average[idx.global] = sum / 4;  
      }  
);  
  
for (int i = 0; i < 4; i++) {  
    for (int j = 0; j < 6; j++) {  
        std::cout << average(i,j) << " ";  
    }  
    std::cout << "\n";  
}  
  
// Output:  
// 3 3 8 8 3 3  
// 3 3 8 8 3 3  
// 5 5 2 2 4 4  
// 5 5 2 2 4 4  
// Sample data.  
int sampledata[] = {  
    2, 2, 9, 7, 1, 4,  
    4, 4, 8, 8, 3, 4,  
    1, 5, 1, 2, 5, 2,  
    6, 8, 3, 2, 7, 2};  
  
// The tiles are:  
// 2 2    9 7    1 4  
// 4 4    8 8    3 4  
//  
// 1 5    1 2    5 2  
// 6 8    3 2    7 2  
  
// Averages.  
int averagedata[] = {   
    0, 0, 0, 0, 0, 0,   
    0, 0, 0, 0, 0, 0,   
    0, 0, 0, 0, 0, 0,   
    0, 0, 0, 0, 0, 0,   
};  
  
array_view<int, 2> sample(4, 6, sampledata);  
array_view<int, 2> average(4, 6, averagedata);  
  
parallel_for_each(  
    // Create threads for sample.grid and divide the grid into 2 x 2 tiles.  
    sample.extent.tile<2,2>(),  
    [=](tiled_index<2,2> idx) restrict(amp)  
    {  
        // Create a 2 x 2 array to hold the values in this tile.  
        tile_static int nums[2][2];  
        // Copy the values for the tile into the 2 x 2 array.  
        nums[idx.local[1]][idx.local[0]] = sample[idx.global];  
        // When all the threads have executed and the 2 x 2 array is complete, find the average.  
        idx.barrier.wait();  
        int sum = nums[0][0] + nums[0][1] + nums[1][0] + nums[1][1];  
        // Copy the average into the array_view.  
        average[idx.global] = sum / 4;  
      }  
);  
  
for (int i = 0; i < 4; i++) {  
    for (int j = 0; j < 6; j++) {  
        std::cout << average(i,j) << " ";  
    }  
    std::cout << "\n";  
}  
  
// Output.  
// 3 3 8 8 3 3  
// 3 3 8 8 3 3  
// 5 5 2 2 4 4  
// 5 5 2 2 4 4  
  
```  
  
## Voir aussi  
 [Modificateurs spécifiques Microsoft](../cpp/microsoft-specific-modifiers.md)   
 [Présentation de C\+\+ AMP](../parallel/amp/cpp-amp-overview.md)   
 [parallel\_for\_each, fonction \(C\+\+ AMP\)](../Topic/parallel_for_each%20Function%20\(C++%20AMP\).md)   
 [Procédure pas à pas : Multiplication des matrices](../parallel/amp/walkthrough-matrix-multiplication.md)