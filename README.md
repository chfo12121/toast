# toast
toast function

怎样使用？

放入style

    <style>
        .evil-tip {
            position: fixed;
            top: 0;
            left: 0;
            bottom: 0;
            right: 0;
            display: -webkit-box;
            display: box;
            -webkit-box-pack: center;
            box-pack: center;
            -webkit-box-align: center;
            box-align: center;
            display: -webkit-flex;
            display: flex;
            -webkit-justify-content: center;
            justify-content: center;
            -webkit-align-items: center;
            align-items: center;
            transition: opacity 1555ms;
            opacity: .000001;
            z-index: 9999;
        }
        .evil-tip.see {
            transition-duration: 666ms;
            opacity: 1;
        }
        .evil-tip div {
            background: #000;
            color: #fff;
            text-align: center;
            font-size: 14px;
            line-height: 1.3;
            border-radius: 3px;
            box-shadow: 0 0 5px rgba(0, 0, 0, .3);
            max-width: 77%;
            padding: 10px 5px;
            margin-bottom: 111px;
        }
    </style>

放入script

    <script>
        /**
         * @function tip toast提示，配合样式使用
         * @param {string} words - 要显示的文字
         * @param {(number|'auto')} [period] - toast多久(ms)后消失，如果不传取默认1500ms，传auto，会根据字数自动设置时长
         */
        function tip(words, period) {
            var div = document.createElement('div')
            div.display = 'none'
            div.className = 'evil-tip'
            var divdiv = document.createElement('div')
            div.appendChild(divdiv)
            document.body.appendChild(div)
            var timeout
            div.addEventListener('transitionend', function () {
                if (!div.classList.contains('see')) {
                    div.style.display = 'none'
                }
            })
            div.addEventListener('touchstart', function () {
                div.style.display = 'none'
            });
            (tip = function (words, period) {
                clearTimeout(timeout)
                divdiv.innerHTML = words
                div.style.display = ''
                setTimeout(function () {
                    div.classList.add('see')
                    timeout = setTimeout(function () {
                        div.classList.remove('see')
                    }, period ? period == 'auto' ? 666 + words.length * 88 : period : 1500)
                })
            })(words, period)
        }
    </script>

ok!

document.querySelector('#test').addEventListener('click', function () {
    tip('试试', 'auto')
})
