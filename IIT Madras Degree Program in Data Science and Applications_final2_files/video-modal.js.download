function openVideo(video) {
    let src = video.getAttribute("data-theVideo");
    $('#videoModal').modal('show');
    $('#videoModal iframe').attr('src', src);
}

$('#videoModal button').click(function () {
    $('#videoModal iframe').removeAttr('src');
});

$('#videoModal').on('hidden.bs.modal', function () {
    $('#videoModal iframe').removeAttr('src');
});