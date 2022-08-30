# Build-an-INTERACTIVE-Fade-in-Review-Display-in-JavaScript

##
https://www.youtube.com/watch?v=SQdtEcQ0ll4

##
App.js 
const reviewContainer = document.getElementById('review-container')

// keep the images landscape images 
const reviews = [
    {
        img: "https://thumbs.dreamstime.com/b/confident-smiling-indian-young-business-woman-student-sales-professional-office-employee-hr-teacher-india-standing-arms-192389177.jpg",
        alt: "Profile picture of Indyah Almay",
        text: "I realy enjoy this course! It was fun and interactive as well as educational. I learnt alot!",
        name: "Indyah Almay"
    }
]

function populateDisplay() {
    reviews.forEach(review => {
       const cardElement = document.createElement('div')
       cardElement.classList.add('card')

       cardElement.addEventListener('mouseover', showCard)
       cardElement.addEventListener('mouseleave', blurCard)

       const imageContainer = document.createElement('div')
       imageContainer.classList.add('image-container')
       const imageElement = document.createElement('img')
       imageElement.setAttribute('src', review.img)
       imageElement.setAttribute('alt', review.alt)
       imageContainer.append(imageElement)

       const paragraphElement = document.createElement('p')
       paragraphElement.textContent = reviews.text 
       const nameContainer = document.createElement('div')
       nameContainer.classList.add('name-container')
       nameContainer.textContent = review.name



       cardElement.append(imageContainer, paragraphElement, nameContainer)

       reviewContainer.append(cardElement)
    })
}

populateDisplay()

function showCard () {
    this.classList.add('active')
}


function blurCard () {
    this.classList.remove('active')
}

##

Index.html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>JS Review Display</title>
    <link rel="stylesheet" href="Styles.css">
</head>
<body>
    <div id="review-container"></div>

    <script src="App.js"></script>
</body>
</html>

##

Styles.css
*{
    font-family: "Lucida Sans", Arial, sans-serif;
    color: rgb(79, 79, 79);

}

#review-container{
    display: flex;
    justify-content: center;

}

.card {
    width: 200px;
    height: 290px;
    border-radius: 10px;
    box-shadow: rgba(50, 50, 50, 0.25) 0 6px 12px -2px, rgba(0, 0, 0, 0.3) 0 3px 7px -3px;
    text-align: center;
    display: flex;
    justify-content: center;
    flex-direction: column;
    position: relative;
    align-items: center;
    opacity: 0.3;
    transform: scale(0.8, 0.8);
    transition: all 0.3s ease-in-out;
}

active {
    opacity: 1;
    transform: scale(1, 1);
    transition: all 0.3s ease-in-out;
}

.card p {
    padding: 0 20px;

}

.card .image-container{
    width: 90px;
    height: 90px;
    border-radius: 45px;
    overflow: hidden;


}

.card .image-container img {
    height: 100%;
    margin-left: -25%;

}

.card .name-conteiner{
    position: absolute;
    bottom: 0;
    background-color: rgb(231, 208, 253);
    width: 100%;
    text-align: center;
    padding: 10px 0;

}
