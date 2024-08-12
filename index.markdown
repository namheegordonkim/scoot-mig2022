---
layout: splash
author_profile: false
---

# Learning High-Risk High-Precision Motion Control

*In Proceedings of ACM SIGGRAPH Conference on Motion, Interaction and Games (MIG) 2022*

<style>
div {
    /* border: 1px solid black; */
}

div.author {
    display: flex;
    align-items: center;
}

div.affiliation {
    padding-left: 10px;
    font-size: 18px;
    vertical-align: middle;
}
div.name {
    text-transform: uppercase;
}
span.affiliation {
    size: 1px;
}
p.author {
    margin: 5px 0
}

div.teaser {
    overflow: hidden;
    align: center;
    text-align: center;
    padding-bottom: 10px;
}

img.teaser {
    overflow: hidden;
    width:40%;
    margin-top:-50px;
    margin-bottom: -50px;
    /* margin-left: auto;
    margin-right: auto; */
}

a {
  text-decoration: none;
}

</style>

<div class="authors">
{% for author in site.data.authors %}

<div class="author">
<div class="name">
{% if author.website != "" %}
<a href="{{author.website}}">{{author.name}}</a>
{% else %}
{{author.name}}
{% endif %}
</div>
<div class="affiliation">{{author.affiliation}}</div>
</div>
{% endfor %}
</div>

<div class="teaser">
<img class="teaser" src="{{'/assets/billiards_teaser.gif' | relative_url}}" />
</div>
<div style="text-align: center;">
The variation of the initial condition of the billiards table and the successful trajectories resulting from executing policy output. The red line tracks the movement of the target ball and the white line tracks the movement of the cue ball.
</div>

## Paper: [HTML](https://dl.acm.org/doi/fullHtml/10.1145/3561975.3562943)

Deep reinforcement learning (DRL) algorithms for movement control are typically evaluated and benchmarked on sequential decision tasks where imprecise actions may be corrected with later actions, thus allowing high returns with noisy actions. In contrast, we focus on an under-researched class of high-risk, high-precision motion control problems where actions carry irreversible outcomes, driving sharp peaks and ridges to plague the state-action reward landscape. Using computational pool as a representative example of such problems, we propose and evaluate State-Conditioned Shooting (SCOOT), a novel DRL algorithm that builds on advantage-weighted regression (AWR) with three key modifications: 1) Performing policy optimization only using elite samples, allowing the policy to better latch on to the rare high-reward action samples; 2) Utilizing a mixture-of-experts (MoE) policy, to allow switching between reward landscape modes depending on the state; 3) Adding a distance regularization term and a learning curriculum to encourage exploring diverse strategies before adapting to the most advantageous samples. We showcase our features' performance in learning physically-based billiard shots demonstrating high action precision and discovering multiple shot strategies for a given ball configuration. 

### Summary

We diagnose the difficulty of high-precision motion control by visualizing the reward landscape, which shows sparse, sharp, and multi-modal reward ridges. Capturing the sparse reward ridges requires stringent pruning of negative-advantage samples and capturing multi-modal solution modes requires the use of a mixture model policy. We devise simple modifications to an existing off-policy DRL algorithm--Advantage-Weighted Regression (AWR) to accomodate for these challenges.

<style>
div.figure {
    width: 70%;
    margin-left: auto;
    margin-right: auto;
    align: center;
    text-align: center;
    padding-bottom: 10px;
}
</style>

<div class="figure">
<img src="{{'/assets/billiards_landscape.jpg' | relative_url}}" />
</div>
<div>
<b>Left:</b> a view of a physically-simulated billiards table with 1-dimensional state and action variables. <b>Right:</b> the state-action reward landscape corresponding to the simplified billiards environment. Dark regions indicate high reward at the state-action coordinate. 
</div>

<div class="figure">
<img src="{{'/assets/billiards_summary.jpg' | relative_url }}"/>
</div>
<div>
An overview of policy optimization iterations with a mixture-of-experts policy and elite samples from off-policy experience replay buffer.
</div>

### Cite Us

<div style="display: flex;">
<pre style="line-height: 1.4; overflow: auto; font-size: 0.5rem; ">
@inproceedings{kim2022learning,
    title={Learning High-Risk High-Precision Motion Control},
    author={Kim, Nam Hee and Kirjonen, Markus and H{\"a}m{\"a}l{\"a}inen, Perttu},
    booktitle={Proceedings of the 15th ACM SIGGRAPH Conference on Motion, Interaction and Games},
    pages={1--10},
    year={2022}
}
</pre>
</div>