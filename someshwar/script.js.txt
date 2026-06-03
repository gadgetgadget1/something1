document.addEventListener("DOMContentLoaded", () => {

const counters = document.querySelectorAll(".counter");

counters.forEach(counter => {

const target = +counter.dataset.target;

let count = 0;

const updateCounter = () => {

const increment = target / 100;

if(count < target){

count += increment;

counter.innerText = Math.ceil(count);

requestAnimationFrame(updateCounter);

}else{

counter.innerText = target + "+";

}

};

updateCounter();

});

const observer = new IntersectionObserver(entries => {

entries.forEach(entry => {

if(entry.isIntersecting){

entry.target.style.opacity = "1";
entry.target.style.transform = "translateY(0)";

}

});

},{
threshold:0.2
});

document.querySelectorAll(".card,.stat,.product-box").forEach(el => {

el.style.opacity = "0";
el.style.transform = "translateY(50px)";
el.style.transition = "all 0.8s ease";

observer.observe(el);

});

window.addEventListener("scroll", () => {

const navbar = document.querySelector(".navbar");

if(window.scrollY > 50){

navbar.style.background =
"rgba(5,8,22,0.95)";

navbar.style.boxShadow =
"0 10px 30px rgba(0,0,0,.4)";

}else{

navbar.style.background =
"rgba(5,8,22,.75)";

navbar.style.boxShadow = "none";

}

});

const buttons =
document.querySelectorAll(
".primary-btn,.secondary-btn,.btn-nav"
);

buttons.forEach(btn => {

btn.addEventListener("mouseenter", () => {

btn.style.transform = "translateY(-3px)";

});

btn.addEventListener("mouseleave", () => {

btn.style.transform = "translateY(0)";

});

});

});