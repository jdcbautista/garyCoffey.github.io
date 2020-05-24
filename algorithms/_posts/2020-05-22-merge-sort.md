---
layout: algorithm
title: "Merge Sort"
github_name: "merge_sort"
categories: algorithms
repl_link: 'https://repl.it/repls/GruesomeBossySequences?lite=true'
---
**Code on github**
 <a href="{{ site.data.social-media['github'].href }}{{ site.data.social-media['github'].id }}/{{page.github_name}}" title="{{ site.data.social-media['github'].title }}"><i class="fa {{ site.data.social-media['github'].fa-icon }}"></i></a>

### Description
The problem this algorithm solves is the need to merge to sorted arrays together. 
The examples below 
	 * Example1  merge: [a c e g ] with [ b d f h] would yield [a b c d e f g h] 
	 * Example2  merge: [a f  ] with [ b c  h i] would yield [a b c f h i] 
	 * There is no guarantee about the size of either array. When/if you run out of elements in 
	 * either array, copy all the remaining elements from the nonempty array to the the new array 
	 * preconditions:
	 *          both arrays are sorted low to high
	 *          there are no duplicate values among the two arrays
	 *          either array may be empty
	 * postcondition: an array with all elements from both arrays sorted from low to high
	 * 
	 * You may not use any additional methods, sorting routines etc
	 * For full credit, your solution may only go through each array one time ( so in particular - no nested loops)
	 * 
	 * You will need to create a new array inside the function
	 * You do not have to write this recursively. 
	 */

<iframe height="400px" width="100%" src="{{page.repl_link}}?lite=true" scrolling="no" frameborder="no" allowtransparency="true" allowfullscreen="true" sandbox="allow-forms allow-pointer-lock allow-popups allow-same-origin allow-scripts allow-modals"></iframe>
