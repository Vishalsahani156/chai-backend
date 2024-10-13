import { asyncHandler } from "../util/asyncHandler"
import {User}from "../model/user.models"
import {ApiError} from "../util/ApiError.js"
import {ApiResponse} from "../util/ApiResponse.js"
import {uplodeOnCloudinary} from "../util/cloudinary.js"

//TODO: get all videos based on query, sort, 
// TODO: get all videos based on query, sort
const getAllVideo = asyncHandler(async (req, res) => {
    const { page = 1, limit = 10, query = "", sortBy = "createdAt", sortTypes = "desc", userId } = req.query;
    
    const options = {
      page: Number(page),
      limit: Number(limit),
      sort: { [sortBy]: sortTypes === "asc" ? 1 : -1 }
    };
  
    const filter = query ? { title: { $regex: query, $options: "i" } } : {}; // filter by query in title
    if (userId) {
      filter.userId = userId; // If userId is provided, filter by userId
    }
  
    const videos = await Video.paginate(filter, options);
    res.status(200).json({
      success: true,
      videos,
    });
  });
// TODO: get video, upload to cloudinary, create video
const publicVideo = asyncHandler(async (req, res) => {
    const { title, description } = req.body
    if(!req.files){
     throw new ApiError(400,"user can not provide  the files ")
    }
    const result=await  uplodeOnCloudinary.upload(req.files.path)


})
//TODO: get video by id
const videoId = asyncHandler(async (req, res) => {
    const { videId } = req.params
})
//TODO: update video details like title, description, thumbnail
const updateVideoDetels = asyncHandler(async (req, res) => {
    const { viodeId } = req.params

})
//TODO: delete video
const deleteVideo = asyncHandler(async (req, res) => {
    const { videoId } = req.params


})
// togglePublishStatus
const togglePublishStatus = asyncHandler(async (req, res) => {
    const { videoId } = req.params



})

export default {

};
